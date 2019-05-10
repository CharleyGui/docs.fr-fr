---
title: 'Procédure : déchiffrer des éléments XML avec des clés asymétriques'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c1891bf91095a5c09257b795c66e96dbc2bf69d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64653882"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Procédure : déchiffrer des éléments XML avec des clés asymétriques
Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer et déchiffrer un élément d'un document XML.  Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.  Pour plus d’informations sur la norme de chiffrement XML, consultez la recommandation du World Wide Web Consortium (W3C) [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).  
  
 L’exemple de cette procédure déchiffre un élément XML qui a été chiffré à l’aide des méthodes décrites dans [Comment : Chiffrer des éléments XML avec des clés asymétriques](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Il trouve un <`EncryptedData`> élément, déchiffre l’élément, puis remplace l’élément avec l’élément XML en texte brut d’origine.  
  
 Cet exemple déchiffre un élément XML à l'aide de deux clés.  Il récupère une clé privée RSA générée précédemment à partir d’un conteneur de clé, et utilise la clé RSA pour déchiffrer une clé de session stockées dans le <`EncryptedKey`> élément de la <`EncryptedData`> élément.  L'exemple utilise ensuite la clé de session pour déchiffrer l'élément XML.  
  
 Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Pour déchiffrer un élément XML avec une clé asymétrique  
  
1. Créez un objet <xref:System.Security.Cryptography.CspParameters> et spécifiez le nom du conteneur de clé.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Récupérez une clé asymétrique générée précédemment à partir du conteneur à l'aide de l'objet <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  La clé est automatiquement récupérée depuis le conteneur de clé quand vous passez l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedXml> pour déchiffrer le document.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. Ajoutez un mappage nom/clé pour associer la clé RSA à l'élément dans le document qui doit être déchiffré.  Vous devez utiliser le même nom de clé que celui que vous avez utilisé quand vous avez chiffré le document.  Notez que ce nom est différent du nom utilisé pour identifier la clé dans le conteneur de clé spécifié à l'étape 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. Appelez le <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> méthode pour déchiffrer le <`EncryptedData`> élément.  Cette méthode utilise la clé RSA pour déchiffrer la clé de session et utilise automatiquement la clé de session pour déchiffrer l'élément XML.  Elle remplace également automatiquement le <`EncryptedData`> élément avec le texte brut d’origine.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. Enregistrez le document XML  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Exemple  
 Cet exemple suppose qu'un fichier nommé `test.xml` se trouve dans le même répertoire que le programme compilé.  Il suppose également que `test.xml` contient un élément XML qui a été chiffré à l’aide des techniques décrites dans [Comment : Chiffrer des éléments XML avec des clés asymétriques](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.  
  
- Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Ne stockez jamais une clé de chiffrement symétrique en texte brut et ne transférez jamais une clé symétrique d'un ordinateur à l'autre en texte brut.  De plus, la clé privée d'une paire de clés asymétriques ne doit jamais être stockée ni transférée en texte brut.  Pour plus d’informations sur les clés de chiffrement symétriques et asymétriques, consultez [génération de clés pour le chiffrement et déchiffrement](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 N'incorporez jamais une clé directement dans votre code source.  Les clés incorporées peuvent être lues facilement à partir d’un assembly à l’aide de [Ildasm.exe (désassembleur IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou en ouvrant l’assembly dans un éditeur de texte tel que le bloc-notes.  
  
 Quand vous avez terminé d'utiliser une clé de chiffrement, effacez-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.  Les clés de chiffrement peuvent parfois être lues à partir de la mémoire par un débogueur ou à partir d'un disque dur si l'emplacement de mémoire est paginé sur le disque.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Cryptography.Xml>
- [Guide pratique pour Chiffrer des éléments XML avec des clés asymétriques](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
