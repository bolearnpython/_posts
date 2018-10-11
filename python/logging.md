---
title: logging
tags: log,logging
grammar_cjkRuby: true
---
# logging
## 使用
    import logging

    # 创建一个logger
    logger = logging.getLogger('mylogger')
    logger.setLevel(logging.DEBUG)

    # 创建一个handler，用于写入日志文件
    fh = logging.FileHandler('d://test.log')
    fh.setLevel(logging.DEBUG)

    # 再创建一个handler，用于输出到控制台
    ch = logging.StreamHandler()
    ch.setLevel(logging.DEBUG)

    # 定义handler的输出格式
    formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
    fh.setFormatter(formatter)
    ch.setFormatter(formatter)

    # 给logger添加handler
    logger.addHandler(fh)
    logger.addHandler(ch)

    # 记录一条日志
    logger.info('foorbar')

## 导入配置
    import logging
    from logging.config import dictConfig

    logging_config = dict(
        version = 1,
        formatters = {
            'f': {'format':
                  '%(asctime)s %(name)-12s %(levelname)-8s %(message)s'}
            },
        handlers = {
            'h': {'class': 'logging.StreamHandler',
                  'formatter': 'f',
                  'level': logging.DEBUG}
            },
        loggers = {
            'root': {'handlers': ['h'],
                     'level': logging.DEBUG}
            }
    )

    dictConfig(logging_config)

    logger = logging.getLogger()
    logger.debug('often makes a very good meal of %s', 'visiting tourists')



## logging基本配置

    import logging
    # 创建一个log.log日志文件
    logging.basicConfig(filename='d:\\log.log',
                        # 格式化的字符串
                        format='%(asctime)s - %(name)s - %(levelname)s - %(module)s: %(message)s',
                        # 时间
                        datefmt='%Y-%m-%d %H:%M:%S %p',
                        # 错误级别
                        level=logging.DEBUG
                        )
    filemode='a'

    logging.critical('critical')
    logging.error('error')
    logging.warning('warning')
    logging.info('info')
    logging.debug('debug')
    logging.log(logging.INFO, 'NOTSET')