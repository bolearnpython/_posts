---
title: image相关
tags: 验证码,PIL
---
#  image相关
`sudo apt-get install tesseract-ocr  # 安装语言支持 tesseract-ocr-chi-sim`

## PIL
	from PIL import Image, ImageFilter, ImageDraw, ImageFont, ImageEnhance, ImageFilter
	w, h = image.size
	box = (p1, p2, p3, p4)
	image = image.crop(box)
	image.show()
	image.thumbnail((size1, size2), Image.ANTIALIAS)#压缩
	image.show()
	image = image.rotate(jiaodu)
	image.show()
	image = image.convert('L')  #灰度
	image.filter(ImageFilter.DETAIL)#过滤
	draw = ImageDraw.Draw(image)#写字
	draw.text((p1, p2), text)
	image.show()
	im.resize((128, 128))#resize
	im.rotate(45) #45度 顺时针
	im.transpose(Image.ROTATE_90)# 旋转90度
	image = image.convert('1')
	image = image.convert('P')  # 虚化
	image = image.convert('LA')#怀旧
	def 图片拼接(image1, image2):
		images = (image1, image2)
		w, h = image1.size
		target = Image.new('RGB', (w * 2, h))
		left = 0
		right = w
		for image in images:
			temp = image.resize((w, h), Image.ANTIALIAS)
			target.paste(temp, (left, 0, right, h))
			left += w
			right += w
		target.show()
	def 图片锐化(image, qiangdu):
		enhancer = ImageEnhance.Sharpness(image)
		enhancer.enhance(qiangdu).show()

	def 图片色彩增强(image, qiangdu):
		enhancer = ImageEnhance.Color(image)
		enhancer.enhance(qiangdu).show()

	def 图片亮度增强(image, qiangdu):
		enhancer = ImageEnhance.Brightness(image)
		enhancer.enhance(qiangdu).show()

	def 图片对比度增强(image, qiangdu):
		enhancer = ImageEnhance.Contrast(image)
		enhancer.enhance(qiangdu).show()

	def 图片BlUR(image):
		image = image.filter(ImageFilter.BLUR)
		image.show()

	def 图片MinFilter(image):
		image = image.filter(ImageFilter.MinFilter)
		image.show()

	def 图片转换黑白线条(image):
		image = image.filter(ImageFilter.CONTOUR)
		image.show()

	def 图片EMBOSS(image):
		image = image.filter(ImageFilter.EMBOSS)
		image.show()

	def 图片FIND_EDGES(image):
		image = image.filter(ImageFilter.FIND_EDGES)
		image.show()

## 验证码生成
	from captcha.image import ImageCaptcha
	number = '0123456789'
	alphabet = 'abcdefghijklmnopqrstuvwxyz'
	char_set = number  # +alphabet+alphabet.upper()
	# 生成字符对应的验证码


	def gen_captcha_text_and_image():
	    image = ImageCaptcha()
	    captcha_text = [random.choice(char_set)for i in range(4)]
	    captcha_text = ''.join(captcha_text)
	    captcha = image.generate(captcha_text)
	    captcha_image = Image.open(captcha)
	    captcha_image = captcha_image.convert('L')
	    captcha_image = captcha_image.resize([128, 64])
	    captcha_image = np.array(captcha_image)/255.0
	    return captcha_text, captcha_image
## 验证码
	from pyocr import pyocr
	tools = pyocr.get_available_tools()[:]
	tools[0].get_name()
	tools[0].image_to_string(im, lang='eng')
	tools[0].image_to_string(im, lang='chi_sim')


	import requests
	import pytesseract as ocr
	from PIL import Image
	from io import BytesIO
	def retrive_img(url):
	    resp = requests.get(url)
	    img_fp = BytesIO(resp.content)
	    return Image.open(img_fp)
	def process_img(img, threshold=140):
	    # 灰度转换
	    img = img.convert('L')
	    # 二值化
	    pixels = img.load()
	    for x in range(img.width):
	        for y in range(img.height):
	            pixels[x,y] = 255 if pixels[x,y] > threshold else 0
	    return img
	def recognize(img, lang='eng'):
	    return ocr.image_to_string(img, lang)
	if __name__ == '__main__':
	    img = process_img(retrive_img('http://zfcg.fjqz.gov.cn/ucapqzzfcg/portal/validate/img2.jsp'))
	    print(recognize(img))
	    img.show()
