	������xtest�ж����㷨�ӿڵĲ��Զ���ͨ��һ��һ������ɵģ�����
�����㷨�ľ���ʹ��ʱ�������ȡ�÷�ʽ�����ǽ�����ͨ��CA���ݽoTA��
Ȼ����TA���һ����ɵ��㷨������Ȼ�󷵻ؼ��ܣ����ܣ�ǩ������ǩ��
�����CA�С�
	��TA�а�����RSA1024/RSA2048/HMAC/SHA1/SHA256/AES/PBKDF2/RAMDON��
�㷨�ľ���ʹ�ò�����ֻҪ��CA�˽���Ҫʹ���㷨���м��ܵ����ݴ��ݽo
TEE��ִ��֮����ܵõ�ʹ�ø��㷨������Ľ�������������REE��ʹ��
����CA����TA����������㷨����ľ����������Ҫ����linux�е�shell
������ָ�����qemu+OP-TEE�Ļ����²���ͨ�����㷨����ʹ�õ���key
���ᱣ����TA�С�
	��ʹ�ù����������κ����������ϵ:shuaifengyun@126.com
1. RSA1024�㷨��ʹ��
	encrypt operation(���ܲ���,ʹ��rsa1024 public key��������)ָ�����£�
		basicAlgUse rsa1024 enc
	decrypt operation(���ܲ���,ʹ��rsa1024 private key��������)ָ�����£�
		basicAlgUse rsa1024 dec
	sign operation(ǩ������,ʹ��rsa1024 private key��������)ָ�����£�
		basicAlgUse rsa1024 sign
	verify operation(��ǩ����,ʹ��rsa1024 public key��������)ָ�����£�
		basicAlgUse rsa1024 verify

2. RSA2048�㷨��ʹ��
	encrypt operation(���ܲ���,ʹ��rsa2048 public key��������)ָ�����£�
		basicAlgUse rsa2048 enc
	decrypt operation(���ܲ���,ʹ��rsa2048 private key��������)ָ�����£�
		basicAlgUse rsa2048 dec
	sign operation(ǩ������,ʹ��rsa2048 private key��������)ָ�����£�
		basicAlgUse rsa2048 sign
	verify operation(��ǩ����,ʹ��rs2048 public key��������)ָ�����£�
		basicAlgUse rsa2048 verify

3. RANDOM��ʹ��
	��TA����ָ�����ȵ������ָ������(numΪҪ������������ĳ���)��
	basicAlgUse random [num]

4. AES�㷨��ʹ��
	AES��CBCģʽ���м��ܲ���ָ�����£�
		basicAlgUse aes enc cbc
	AES��ECBģʽ���м��ܲ���ָ�����£�
		basicAlgUse aes enc ecb
	AES��CTRģʽ���м��ܲ���ָ�����£�
		basicAlgUse aes enc ctr
	AES��CTSģʽ���м��ܲ���ָ�����£�
		basicAlgUse aes enc cts
	AES��CBCģʽ���н��ܲ���ָ�����£�
		basicAlgUse aes dec cbc
	AES��ECBģʽ���н��ܲ���ָ�����£�
		basicAlgUse aes dec ecb
	AES��CTRģʽ���н��ܲ���ָ�����£�
		basicAlgUse aes dec ctr
	AES��CTSģʽ���н��ܲ���ָ�����£�
		basicAlgUse aes dec cts

5. HMAC��ʹ��
	ʹ��HMAC����ָ�����ȵ����ݣ�password��salt��TA���趨����ָ������
	(len��ָ�����ظ�CA�����ݵĳ��ȣ�count��ָ�������ѭ������)��
		basicAlgUse hmac [len] [count]

6. BASE64��ʹ��
	ʹ��base64���м���(��TA��ʹ���������ʵ��)ָ�����£�
		basicAlgUse base64 enc
	ʹ��base64���н���(��TA��ʹ���������ʵ��)ָ�����£�
		basicAlgUse base64 dec

7. PBKDF2��ʹ��
	ʹ��PBKDF2��һ����generate keyʱ��ʹ�ã�numΪҪ���ظ�CA�����ݵĳ��ȣ�
	pbkdf2�㷨��ʹ�õ�salt, passworkd, countֵ����TA�б��趨��ָ�����£�
		basicAlgUse pbkdf [num]
