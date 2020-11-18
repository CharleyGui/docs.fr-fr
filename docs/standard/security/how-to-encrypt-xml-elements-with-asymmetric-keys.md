---
title: 'Procédure : chiffrer des éléments XML avec des clés asymétriques'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSA class
- asymmetric keys [.NET]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- encryption [.NET], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: 7254079c12926dbe055ea58f045862afd17bab1e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820265"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Procédure : chiffrer des éléments XML avec des clés asymétriques

Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.  Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.  Pour plus d’informations sur la norme de chiffrement XML, consultez la spécification World Wide Web Consortium (W3C) pour le chiffrement XML situé dans <https://www.w3.org/TR/xmldsig-core/> .  
  
 Vous pouvez utiliser le chiffrement XML pour remplacer tout élément XML ou tout document comportant un élément <`EncryptedData`> qui contient des données XML chiffrées.  L' `EncryptedData` élément <> peut également contenir des sous-éléments qui incluent des informations sur les clés et les processus utilisés pendant le chiffrement.  Le chiffrement XML permet à un document de contenir plusieurs éléments chiffrés et permet à un élément d'être chiffré plusieurs fois.  L’exemple de code de cette procédure montre comment créer un `EncryptedData` élément <> avec plusieurs autres sous-éléments que vous pouvez utiliser ultérieurement pendant le déchiffrement.  
  
 Cet exemple chiffre un élément XML à l'aide de deux clés.  Il génère une paire de clés publique/privée RSA et l'enregistre dans un conteneur de clé sécurisé.  L’exemple crée ensuite une clé de session distincte à l’aide de l’algorithme Advanced Encryption Standard (AES).  L'exemple utilise la clé de session AES pour chiffrer le document XML, puis utilise la clé publique RSA pour chiffrer la clé de session AES.  Enfin, l’exemple enregistre la clé de session AES chiffrée et les données XML chiffrées dans le document XML au sein d’un nouvel `EncryptedData` élément <>.  
  
 Pour déchiffrer l'élément XML, vous devez récupérer la clé privée RSA du conteneur de clé, l'utiliser pour déchiffrer la clé de session et ensuite utiliser la clé de session pour déchiffrer le document.  Pour plus d’informations sur le déchiffrement d’un élément XML chiffré à l’aide de cette procédure, consultez [Comment : déchiffrer des éléments XML avec des clés asymétriques](how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Pour chiffrer un élément XML avec une clé asymétrique  
  
1. Créez un objet <xref:System.Security.Cryptography.CspParameters> et spécifiez le nom du conteneur de clé.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Générez une clé symétrique à l'aide de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  La clé est automatiquement enregistrée dans le conteneur de clé quand vous passez l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Cette clé sera utilisée pour chiffrer la clé de session AES et peut être récupérée ultérieurement pour la déchiffrer.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.  L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à chiffrer.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. Recherchez l'élément spécifié dans l'objet <xref:System.Xml.XmlDocument>, puis créez un objet <xref:System.Xml.XmlElement> pour représenter l'élément que vous voulez chiffrer. Dans cet exemple, l'élément `"creditcard"` est chiffré.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. Créez une clé de session en utilisant la classe <xref:System.Security.Cryptography.Aes>.  Cette clé chiffrera l'élément XML, puis sera chiffrée et placée dans le document XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. Créez une instance de la classe <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez-la pour chiffrer l'élément spécifié à l'aide de la clé de session.  La méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> retourne l'élément chiffré en tant que tableau d'octets chiffrés.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedData> et ajoutez-lui l'identificateur d'URL de l'élément XML chiffré.  Cet identificateur d'URL informe la partie chargée du déchiffrement que le code XML contient un élément chiffré.  Vous pouvez utiliser le champ <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pour spécifier l'identificateur d'URL.  L’élément XML en texte brut sera remplacé par un `EncryptedData` élément <> encapsulé par cet <xref:System.Security.Cryptography.Xml.EncryptedData> objet.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. Créez un objet <xref:System.Security.Cryptography.Xml.EncryptionMethod> qui sera initialisé vers l'identificateur d'URL de l'algorithme de chiffrement utilisé pour générer la clé de session.  Passez l'objet <xref:System.Security.Cryptography.Xml.EncryptionMethod> à la propriété <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedKey> devant contenir la clé de session chiffrée.  Chiffrez la clé de session, ajoutez-la à l'objet <xref:System.Security.Cryptography.Xml.EncryptedKey>, puis entrez un nom de clé de session et une URL de d'identificateur de clé.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Créez un objet <xref:System.Security.Cryptography.Xml.DataReference> qui mappe les données chiffrées à une clé de session particulière.  Cette étape facultative vous permet de spécifier facilement que plusieurs parties d'un document XML ont été chiffrées par une même clé.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Ajoutez la clé chiffrée pour l'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Créez un objet <xref:System.Security.Cryptography.Xml.KeyInfo> pour spécifier le nom de la clé RSA.  Ajoutez-le à l'objet <xref:System.Security.Cryptography.Xml.EncryptedData>. Cela permet à la partie chargée du déchiffrement de trouver la clé asymétrique à utiliser pour le déchiffrement de la clé de session.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Ajoutez les données d'élément chiffrées à l'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Remplacez l'élément de l'objet <xref:System.Xml.XmlDocument> d'origine par l'élément <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Enregistrez l'objet <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Dans un projet qui cible .NET Framework, incluez une référence à `System.Security.dll` .

- Dans un projet qui cible .NET Core ou .NET 5, installez le package NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).
  
- Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-security"></a>Sécurité .NET

Ne stockez jamais une clé de chiffrement symétrique en texte brut et ne transférez jamais une clé symétrique d'un ordinateur à l'autre en texte brut.  De plus, la clé privée d'une paire de clés asymétriques ne doit jamais être stockée ni transférée en texte brut.  Pour plus d’informations sur les clés de chiffrement symétriques et asymétriques, consultez [génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md).  
  
N'incorporez jamais une clé directement dans votre code source.  Les clés incorporées peuvent être facilement lues à partir d’un assembly à l’aide de l' [Ildasm.exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) ou en ouvrant l’assembly dans un éditeur de texte tel que le bloc-notes.  
  
Quand vous avez terminé d'utiliser une clé de chiffrement, effacez-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.  Les clés de chiffrement peuvent parfois être lues à partir de la mémoire par un débogueur ou à partir d'un disque dur si l'emplacement de mémoire est paginé sur le disque.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de chiffrement](cryptography-model.md)
- [services de chiffrement](cryptographic-services.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)- <xref:System.Security.Cryptography.Xml>
- [Comment : déchiffrer des éléments XML avec des clés asymétriques](how-to-decrypt-xml-elements-with-asymmetric-keys.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
