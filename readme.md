# Neo-ThinSDK(typesciprt)


Neo-ThinSDK ʹ��MIT��ԴЭ��

ʹ��typescript��������Ҫ������ Ϊ NEO��ҳǮ�������ṩ����ļ��ܷ�����

�������ǵĲ�Ʒʹ��typescript������neonjs��Ȼ�ܰ�����������js��Դ�룬���������ǵ�����

## �鿴����
http://sdk.nel.group/

## Neo-ThinSDK ����
### ǩ���㷨
WIF<->˽Կ->��Կ->��Կ->�û���ַ��֤�ű�->�ű�ɢ��<->Address
һϵ�м���

ǩ�� ��ǩ ����
### Ǯ�����
NEP2˽Կ����һϵ�м���

NEP6Ǯ���ļ�һϵ�м���
### �������
���׶�д����
### �ű����
�ű�������

�ű�������

## �ű����ɹ淶
NeoThinSDK������һ������

    public EmitParamJson(param: any): ScriptBuilder {
            if (typeof param === "number")//bool ��С����
            {
                this.EmitPushNumber(new Neo.BigInteger(param as number));
            }
            else if (typeof param === "boolean") {
                this.EmitPushBool(param as boolean);
            }
            else if (typeof param === "object") {
                var list = param as any[];
                for (var i = list.length - 1; i >= 0; i--) {
                    this.EmitParamJson(list[i]);
                }
                this.EmitPushNumber(new Neo.BigInteger(list.length));
                this.Emit(ThinNeo.OpCode.PACK);
            }
            else if (typeof param === "string")//���Ӹ�ʽ
            {
               
            }
            else {
                throw new Error("error type:" + typeof param);
            }
            return this;
        }

����ʹ��һ��jsonֱ�����ýű��Ĳ���������˱����ԣ�֧��Ƕ��
���ںܶิ�ӵĲ������ͣ�ֱ�Ӷ�string������һ�׹淶����֧��          

        //�������Ϊstring,��ʵ������ֵ
        //(string) or(str) ��ͷ����ʾ�Ǹ��ַ�����utf8����Ϊbytes
        //(bytes) or([])��ͷ����ʾ����һ��bytearray
        //(address) or(addr)��ͷ����ʾ��һ����ַ��ת��Ϊ�ű�hash
        //(integer) or(int) ��ͷ����ʾ��һ��������
        //(hexinteger) or (hexint) or (hex) ��ͷ����ʾ��һ��16���Ʊ�ʾ�Ĵ�������ת��Ϊbytes���Ƿ���
        //(int256) or (hex256) ��ͷ,��ʾ��һ��������256λ 16���ƴ�����
        //(int160) or (hex160) ��ͷ,��ʾ��һ��������160λ 16���ƴ�����

����
    
    [
        "(str)name",
        [
          "(bytes)0x112233",
          "(hex160)0x1122334455667788990011223344556677889900"
        ]
    ]
<img src=code1.png>

## ����
Neo-thinSDK������Щ��Ŀ

[google CryptoJS](https://code.google.com/archive/p/crypto-js/)
��aes����

    <script src="lib/rollup/aes.js"></script>
    <script src="lib/component/aes.js"></script>
    <script src="lib/component/mode-ecb.js"></script>
    <script src="lib/component/pad-nopadding.js"></script>

[WEbScrypt ��Ŀ](https://github.com/EtherDream/WebScrypt)

    <script src="lib/scrypt.js"></script>