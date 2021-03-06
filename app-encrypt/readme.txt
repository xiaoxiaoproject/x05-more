BASE64 属于编码格式，而非加密算法
	Base64编码要求把3个8位字节（3*8=24）转化为4个6位的字节（4*6=24），之后在6位的前面补两个0，形成8位一个字节的形式。 
	如果剩下的字符不足3个字节，则用0填充，输出字符使用'='，因此编码后输出的文本末尾可能会出现1或2个'='。
　　	为了保证所输出的编码位可读字符，Base64制定了一个编码表，以便进行统一转换。编码表的大小为2^6=64，这也是Base64名称的由来。
	可能出现的字符：0-9 a-z A-Z + /  =
	
	应用：
	1. 将二进制数据转换为字符串形式在网络上进行传输。如，将图片转为base64字符串在网络上传输
	2. 对明文进行简单转换，使其没有可读性
	3. 对摘要进行转换，得到另一种形式的字符串（破译的前提是，破译者能识别出破译的结果确实是明文，也即破译的结果必须容易辨认。如果明文加密前进行了压缩处理，辨认将变得困难）
	4. 一般，对MD5哈希值再进行BASE64转换
	
	结论：
	1. base64转换后的字符串长度比原文长1/4
	2. base64转换后的字符串长度为4的整数倍
	
散列算法
MD5 Message Digest Algorithm5，信息摘要算法

SHA Secure Hash Algorithm，安全散列算法

【对称加密算法-加密、解密使用的密钥是相同的】
DES		Data Encryption Standard
	密钥长度64位（实际只用了56位）
	
3DES	TripleDES
	密钥长度168位，速度稍慢
	
AES		Advanced Encryption Standard
	密钥长度则可以是128，192或256比特

【非对称加密算法-由公钥和私钥组成密钥对】
RSA
	RSA的安全性依赖于大数分解，一般来说只用于少量数据加密。 
	最常见的用法是：对AES密文进行加密传输。

RSA结合对称加密算法的应用：数字信封
	信息发送方采用对称密钥来加密信息，然后再用接收方的公钥来加密此对称密钥（这部分称为数字信封）再将它和信息一起发送给接收方；
	接收方先用相应的私钥打开数字信封，得到对称密钥，然后使用对称密钥再解开信息。 

【数字签名与数字证书】
DSA
CER
	如果再有一个第三方的认证机构，用MD5还可以防止文件作者的“抵赖”，这就是所谓的数字签名应用。
	对明文进行摘要，对摘要进行加密（使用第三方机构提供的私钥），置入到明文的载体中（如PDF文件），发送给对方；
	对方对文件中的明文进行同样的摘要算法，得到摘要1
	对方从文件中提取加密后的摘要，使用第三方机构的公钥进行解密，得到摘要2
	最后，比较摘要1与摘要2是否相同，如相同，则表示文件内容未被修改。否则，文件被篡改了。
	
	数字签名的意义在于，对传输过来的数据进行校验。确保数据在传输工程中不被修改。

【公钥与私钥】



