---
title: 'Comment : déchiffrer des éléments XML avec les certificats X.509'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
ms.openlocfilehash: 46fbefbf7a427ec0d60a34ecc2166f8499d08575
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708886"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Comment : déchiffrer des éléments XML avec les certificats X.509
Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer et déchiffrer un élément d'un document XML.  Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.  Pour plus d’informations sur la norme de chiffrement XML, consultez la spécification World Wide Web Consortium (W3C) pour le chiffrement XML situé sur <https://www.w3.org/TR/xmldsig-core/>.  
  
 Cet exemple déchiffre un élément XML qui a été chiffré à l’aide des méthodes décrites dans : [Comment : chiffrer des éléments XML avec des certificats X. 509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Il trouve une <`EncryptedData`élément >, déchiffre l’élément, puis remplace l’élément par l’élément XML en texte brut d’origine.  
  
 L'exemple de code de cette procédure déchiffre un élément XML à l'aide d'un certificat X.509 depuis le magasin de certificats local du compte d'utilisateur actuel.  L’exemple utilise la méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> pour récupérer automatiquement le certificat X. 509 et déchiffrer une clé de session stockée dans le <`EncryptedKey`élément > de l’élément <`EncryptedData`>.  La méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> utilise ensuite automatiquement la clé de session pour déchiffrer l'élément XML.  
  
 Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>Pour déchiffrer un élément XML avec un certificat X.509  
  
1. Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.  L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à déchiffrer.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedXml> en passant l'objet <xref:System.Xml.XmlDocument> au constructeur.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. Déchiffrez le document XML à l'aide de la méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. Enregistrez l'objet <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
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
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.  
  
- Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Le certificat X.509 utilisé dans cet exemple sert à des fins de test uniquement.  Les applications doivent utiliser un certificat X.509 généré par une autorité de certification approuvée ou utiliser un certificat généré par le serveur de certificats Microsoft Windows.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Cryptography.Xml>
- [Comment : chiffrer des éléments XML avec des certificats X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
