# UBLTR 1.2.1 C# Library
GİB e-fatura, e-arşiv için gerekli olan UBLTR class yapısı


Gelir İdaresi Başkanlığına ait olan siteden indirilen UBL-TR1.2.1 paketine ait olan xsd dosyaları cs dosyası oluşturuldu 

https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBL-TR1.2.1_Paketi.zip

Kullanılan xsd.exe komutu aşağıdaki gibidir.
```
xsd.exe ..\common\UBL-CommonExtensionComponents-2.1.xsd ..\common\UBL-CommonBasicComponents-2.1.xsd ..\common\UBL-CommonAggregateComponents-2.1.xsd ..\common\UBL-UnqualifiedDataTypes-2.1.xsd ..\common\CCTS_CCT_SchemaModule-2.1.xsd .\UBL-Invoice-2.1.xsd /c /n:UBLTR.Invoice_2_1
```


Library .Net Standart olarak hazırlandı.
Yani hem .Net Framwork projelerinde hemde .Net Core projelerinde kullanabilirsiniz.


# Kullanım örneği

```
using System;
using UBLTR.Invoice_2_1;

namespace ConsoleSample
{
    class Program
    {
        static void Main(string[] args)
        {
            // örnek invoice nesnesi oluşturuyoruz
            InvoiceType invoice = new InvoiceType();
            invoice.UUID = new UUIDType();
            invoice.UUID.Value = "GIB2020000000001";

            //serialize örneği            
            string xml = invoice.CreateXml();

            //Deserialize örneği
            var b = InvoiceType.Create(xml);
        }
    }
}
```
