---
title: scrapy img 
tags: scrapy,img
grammar_cjkRuby: true
---

## img
    将所有下载的图片转换成通用的格式（JPG）和模式（RGB）
    避免重新下载最近已经下载过的图片
    缩略图生成
    检测图像的宽/高，确保它们满足最小限制
## items
    class MyItem(scrapy.Item):
        image_urls = scrapy.Field()
        images = scrapy.Field()
## setting
    ITEM_PIPELINES = {'scrapy.contrib.pipeline.images.ImagesPipeline': 1}
    IMAGES_STORE = '/path/to/valid/dir'
    #90天的图片失效期限
    IMAGES_EXPIRES = 90
    #缩略图生成
    IMAGES_THUMBS = {
       'small': (50, 50),
       'big': (270, 270),
    }
    #滤出小图片
    IMAGES_MIN_HEIGHT = 110
    IMAGES_MIN_WIDTH = 110

## 定制图片管道的例子
    import scrapy
    from scrapy.contrib.pipeline.images import ImagesPipeline
    from scrapy.exceptions import DropItem
    class MyImagePipelines(ImagesPipeline):
        def get_media_requests(self, item, info):
                for image_url in item['image_urls']:
                    # 这里我把item传过去,因为后面需要用item里面的书名和章节作为文件名
                    yield scrapy.Request(image_url, meta={'item': item})
        def item_completed(self, results, item, info):
            image_paths = [x['path'] for ok, x in results if ok]
            if not image_paths:
                raise DropItem("Item contains no images")
            return item
        def file_path(self, request, response=None, info=None):
            item = request.meta['item']
            # 从URL提取图片的文件名
            image_guid = request.url.split('/')[-1]
            # 拼接最终的文件名,格式:full/{书名}/{章节}/图片文件名.jpg
            filename = u'full/{0[bookname]}/{0[chapter]}/{1}'.format(item, image_guid)
            return filename