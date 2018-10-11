---
title: python加解密
tags: hash,模板rsa,aes,加密,解密
---
# 加密
## hash
    import hashlib
    sha1 = hashlib.sha1()
    sha1.update('how to use sha1 in '.encode())
    print(sha1.hexdigest())
    md5 = hashlib.md5()
    md5.update('how to use md5 in'.encode())
    print(md5.hexdigest())
## base64
    import base64
    base64.b64encode(b'binary\x00string')
    base64.b64decode('YmluYXJ5AHN0cmluZw==')
## RSA
    import rsa
    # 生成密钥
    (pubkey, privkey) = rsa.newkeys(1024)
    message = 'hello'
    crypto = rsa.encrypt(message.encode(), pubkey)
    message = rsa.decrypt(crypto, privkey).decode()
    print(message)
    # 签名
    signature = rsa.sign(message.encode(), privkey, 'SHA-1')
    # 公钥验证
    rsa.verify(message.encode(), signature, pubkey)

    rsaPublickey = int(pubkey, 16)
    key = rsa.PublicKey(rsaPublickey, int('10001', 16))
    sp = rsa.encrypt(pw.encode("utf-8"), key)
    sp = binascii.b2a_hex(sp)

## AES
    import base64
    from cryptography.hazmat.primitives import padding
    from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
    from cryptography.hazmat.backends import default_backend
    key = b'0123456789abcdef'
    iv = b'0123456789abcdef'
    text = b'Attack at dawn'
    # 转pad
    padder = padding.PKCS7(algorithms.AES.block_size).padder()
    padded_data = padder.update(text) + padder.finalize()
    padded_data = padded_data

    cipher = Cipher(algorithms.AES(key), modes.CBC(iv), backend=default_backend())

    encryptor = cipher.encryptor()
    ct = encryptor.update(padded_data) + encryptor.finalize()
    ct_base64 = base64.b64encode(ct)
    print(ct_base64)

    decryptor = cipher.decryptor()
    padded_data = decryptor.update(ct) + decryptor.finalize()
    # 逆转pad
    unpadder = padding.PKCS7(algorithms.AES.block_size).unpadder()
    data = unpadder.update(padded_data)
    text = data + unpadder.finalize()
    print(text)

## binascii
    import binascii
    a = b'worker'
    c = binascii.hexlify(a)
    print(c)
    # 这个功能和a2b_hex()一样
    print(binascii.unhexlify(c))
    a2b_uu(string)                              将以ascii编码的一行数据转化为二进制, 并且返回二进制数据.
    b2a_uu(data)                                将二进制数据转化为一行以ascii编码的字符, date的最大长度为45.
    a2b_base64(string)                          将一块base64的数据转换为二进制数据, 并返回该二进制数据
    b2a_base64(string)                          与上面相反
    a2b_hqx(string)                             binhex4格式化的ASCII数据转换为二进制, 没有做RLE解压.
    b2a_hqx(data)                               与上相反
    rledecode_hqx(data)                         按照binhex4标准, 对data执行RLE解压
    rlecode_hqx(data)                           对data执行binhex方式的压缩, 并返回结果
    crc_hqx(data, crc)                          计算data的binhex4的crc值
    crc32(data[, crc])                          根据crc, 计算crc32(32位检验和数据, 然后将结果 & 0xffffffff(为了在所有Python版本中生成相同的结果, 具体不清楚, 求指导…)
    a2b_qp(string[, header])                    quoted - printable data->bin, 并返回
    b2a_qp(data[, quotetabs, istext, header])   与上面相反
    hexlify(data)                               返回二进制数据的16进制的表现形式
    unhexlify(hexstr)                           与上面相反

