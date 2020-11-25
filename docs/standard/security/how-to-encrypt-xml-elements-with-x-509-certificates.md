---
title: 'Procédure : chiffrer des éléments XML avec des certificats X.509'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: a336997a8cb81f1838d9c5b1ec82bbb04326ed0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729328"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Procédure : chiffrer des éléments XML avec des certificats X.509

Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.  Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.  Pour plus d’informations sur la norme de chiffrement XML, consultez la spécification World Wide Web Consortium (W3C) pour le chiffrement XML situé dans <https://www.w3.org/TR/xmldsig-core/> .  
  
 Vous pouvez utiliser le chiffrement XML pour remplacer tout élément XML ou tout document comportant un élément <`EncryptedData`> qui contient des données XML chiffrées. L'élément <`EncryptedData`> peut contenir des sous-éléments qui incluent des informations sur les clés et les processus utilisés pendant le chiffrement.  Le chiffrement XML permet à un document de contenir plusieurs éléments chiffrés et permet à un élément d'être chiffré plusieurs fois.  L'exemple de code de cette procédure vous montre comment créer un élément <`EncryptedData`> avec plusieurs sous-éléments que vous pouvez utiliser ultérieurement pendant le déchiffrement.  
  
Cet exemple chiffre un élément XML à l'aide de deux clés. L’exemple récupère par programme un certificat et l’utilise pour chiffrer un élément XML à l’aide de la <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> méthode. En interne, la méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> crée une clé de session séparée et l'utilise pour chiffrer le document XML. Cette méthode chiffre la clé de session et l'enregistre avec le code XML chiffré dans un nouvel élément <`EncryptedData`>.  

Pour déchiffrer l’élément XML, appelez la <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> méthode, qui récupère automatiquement le certificat X. 509 à partir du magasin et effectue le déchiffrement nécessaire.  Pour plus d’informations sur le déchiffrement d’un élément XML chiffré à l’aide de cette procédure, consultez [Comment : déchiffrer des éléments XML avec les certificats X.509](how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Pour chiffrer un élément XML avec un certificat X.509  

Pour exécuter cet exemple, vous devez créer un certificat de test et l’enregistrer dans un magasin de certificats. Les instructions relatives à cette tâche sont fournies uniquement pour l' [outil de création de certificats Windows (Makecert.exe)](/windows/desktop/SecCrypto/makecert).

1. Utilisez [Makecert.exe](/windows/desktop/SecCrypto/makecert) pour générer un certificat X. 509 de test et le placer dans le magasin de l’utilisateur local. Vous devez générer une clé d'échange et rendre cette clé exportable. Exécutez la commande suivante :  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. Créez un objet <xref:System.Security.Cryptography.X509Certificates.X509Store> et initialisez-le pour ouvrir le magasin de l'utilisateur actuel.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. Ouvrez le magasin en lecture seule.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. Initialisez un <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> avec tous les certificats du magasin.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. Énumérez les certificats du magasin et recherchez le certificat portant le nom approprié.  Dans cet exemple, le certificat se nomme `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. Quand vous avez trouvé le certificat, fermez le magasin.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.  L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à chiffrer.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. Recherchez l'élément spécifié dans l'objet <xref:System.Xml.XmlDocument>, puis créez un objet <xref:System.Xml.XmlElement> pour représenter l'élément que vous voulez chiffrer.  Dans cet exemple, l'élément `"creditcard"` est chiffré.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Créez une instance de la classe <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez-la pour chiffrer l'élément spécifié à l'aide du certificat X.509.  La méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> retourne l'élément chiffré en tant qu'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Remplacez l'élément de l'objet <xref:System.Xml.XmlDocument> d'origine par l'élément <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Enregistrez l'objet <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>Exemple  

 Cet exemple suppose qu'un fichier nommé `"test.xml"` se trouve dans le même répertoire que le programme compilé.  Il suppose également que `"test.xml"` contient un élément `"creditcard"`.  Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Dans un projet qui cible .NET Framework, incluez une référence à `System.Security.dll` .

- Dans un projet qui cible .NET Core ou .NET 5, installez le package NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).
  
- Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-security"></a>Sécurité .NET
  
Le certificat X.509 utilisé dans cet exemple sert à des fins de test uniquement.  Les applications doivent utiliser un certificat X. 509 généré par une autorité de certification approuvée.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de chiffrement](cryptography-model.md)
- [services de chiffrement](cryptographic-services.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [Procédure : déchiffrer des éléments XML avec des certificats X.509](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
