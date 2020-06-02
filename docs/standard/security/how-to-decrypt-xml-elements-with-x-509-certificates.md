---
title: 'Comment : déchiffrer des éléments XML avec les certificats X.509'
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
ms.openlocfilehash: 32a6d95b96bb20571c14c16cc70b944fa3e4032b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277386"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="ebbde-102">Comment : déchiffrer des éléments XML avec les certificats X.509</span><span class="sxs-lookup"><span data-stu-id="ebbde-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="ebbde-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer et déchiffrer un élément d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="ebbde-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="ebbde-104">Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.</span><span class="sxs-lookup"><span data-stu-id="ebbde-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="ebbde-105">Pour plus d’informations sur la norme de chiffrement XML, consultez la spécification World Wide Web Consortium (W3C) pour le chiffrement XML situé dans <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="ebbde-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="ebbde-106">Cet exemple déchiffre un élément XML qui a été chiffré à l’aide des méthodes décrites dans : [Comment : chiffrer des éléments XML avec des certificats X. 509](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ebbde-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="ebbde-107">Il recherche une <`EncryptedData` élément>, déchiffre l’élément, puis remplace l’élément par l’élément XML en texte brut d’origine.</span><span class="sxs-lookup"><span data-stu-id="ebbde-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="ebbde-108">L'exemple de code de cette procédure déchiffre un élément XML à l'aide d'un certificat X.509 depuis le magasin de certificats local du compte d'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ebbde-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="ebbde-109">L’exemple utilise la <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> méthode pour récupérer automatiquement le certificat X. 509 et déchiffrer une clé de session stockée dans l' `EncryptedKey` élément <> de l' `EncryptedData` élément> <.</span><span class="sxs-lookup"><span data-stu-id="ebbde-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="ebbde-110">La méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> utilise ensuite automatiquement la clé de session pour déchiffrer l'élément XML.</span><span class="sxs-lookup"><span data-stu-id="ebbde-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="ebbde-111">Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.</span><span class="sxs-lookup"><span data-stu-id="ebbde-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="ebbde-112">Pour déchiffrer un élément XML avec un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="ebbde-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="ebbde-113">Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.</span><span class="sxs-lookup"><span data-stu-id="ebbde-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="ebbde-114">L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="ebbde-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="ebbde-115">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedXml> en passant l'objet <xref:System.Xml.XmlDocument> au constructeur.</span><span class="sxs-lookup"><span data-stu-id="ebbde-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="ebbde-116">Déchiffrez le document XML à l'aide de la méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebbde-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="ebbde-117">Enregistrez l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="ebbde-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ebbde-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="ebbde-118">Example</span></span>  
 <span data-ttu-id="ebbde-119">Cet exemple suppose qu'un fichier nommé `"test.xml"` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="ebbde-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="ebbde-120">Il suppose également que `"test.xml"` contient un élément `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="ebbde-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="ebbde-121">Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ebbde-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebbde-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ebbde-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="ebbde-123">Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="ebbde-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="ebbde-124">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="ebbde-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ebbde-125">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ebbde-125">.NET Framework Security</span></span>  
 <span data-ttu-id="ebbde-126">Le certificat X.509 utilisé dans cet exemple sert à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="ebbde-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="ebbde-127">Les applications doivent utiliser un certificat X.509 généré par une autorité de certification approuvée ou utiliser un certificat généré par le serveur de certificats Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="ebbde-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbde-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebbde-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="ebbde-129">Comment : chiffrer des éléments XML avec les certificats X.509</span><span class="sxs-lookup"><span data-stu-id="ebbde-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](how-to-encrypt-xml-elements-with-x-509-certificates.md)
