---
title: 'Comment : vérifier les signatures numériques de documents XML'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: fa5e13e4a84a7d5d5c07c63df9079f4a07aebc62
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277139"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="533d2-102">Comment : vérifier les signatures numériques de documents XML</span><span class="sxs-lookup"><span data-stu-id="533d2-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="533d2-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour vérifier les données XML signées avec une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="533d2-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="533d2-104">Les signatures numériques XML (XMLDSIG) vous permettent de vérifier que les données n'ont pas été modifiées après leur signature.</span><span class="sxs-lookup"><span data-stu-id="533d2-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="533d2-105">Pour plus d’informations sur la norme XMLDSIG, consultez la spécification World Wide Web Consortium (W3C) à l’adresse <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="533d2-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
 <span data-ttu-id="533d2-106">L’exemple de code de cette procédure montre comment vérifier une signature numérique XML contenue dans un `Signature` élément <>.</span><span class="sxs-lookup"><span data-stu-id="533d2-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="533d2-107">L'exemple récupère une clé publique RSA d'un conteneur de clé, puis utilise cette clé pour vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="533d2-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="533d2-108">Pour plus d’informations sur la création d’une signature numérique qui peut être vérifiée à l’aide de cette technique, consultez [Comment : signer des documents XML avec des signatures numériques](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="533d2-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="533d2-109">Pour vérifier la signature numérique d'un document XML</span><span class="sxs-lookup"><span data-stu-id="533d2-109">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="533d2-110">Pour vérifier le document, vous devez utiliser la même clé asymétrique que celle utilisée pour la signature.</span><span class="sxs-lookup"><span data-stu-id="533d2-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="533d2-111">Créez un objet <xref:System.Security.Cryptography.CspParameters> et spécifiez le nom du conteneur de clé qui a été utilisé pour la signature.</span><span class="sxs-lookup"><span data-stu-id="533d2-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="533d2-112">Récupérez la clé publique à l'aide de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="533d2-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="533d2-113">La clé est automatiquement chargée depuis le conteneur de clé quand vous passez l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="533d2-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="533d2-114">Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.</span><span class="sxs-lookup"><span data-stu-id="533d2-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="533d2-115">L'objet <xref:System.Xml.XmlDocument> contient le document XML signé à vérifier.</span><span class="sxs-lookup"><span data-stu-id="533d2-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="533d2-116">Créez un objet <xref:System.Security.Cryptography.Xml.SignedXml> et passez-lui l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="533d2-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="533d2-117">Recherchez l' `signature` élément <> et créez un nouvel <xref:System.Xml.XmlNodeList> objet.</span><span class="sxs-lookup"><span data-stu-id="533d2-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="533d2-118">Charge le code XML du premier <`signature` élément> dans l' <xref:System.Security.Cryptography.Xml.SignedXml> objet.</span><span class="sxs-lookup"><span data-stu-id="533d2-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="533d2-119">Vérifiez la signature à l'aide de la méthode <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> et de la clé publique RSA.</span><span class="sxs-lookup"><span data-stu-id="533d2-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="533d2-120">Cette méthode retourne une valeur booléenne qui indique la réussite ou l'échec.</span><span class="sxs-lookup"><span data-stu-id="533d2-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="533d2-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="533d2-121">Example</span></span>  
 <span data-ttu-id="533d2-122">Cet exemple suppose qu'un fichier nommé `"test.xml"` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="533d2-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="533d2-123">Le `"test.xml"` fichier doit être signé à l’aide des techniques décrites dans Guide pratique [pour signer des documents XML avec des signatures numériques](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="533d2-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="533d2-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="533d2-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="533d2-125">Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="533d2-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="533d2-126">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="533d2-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="533d2-127">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="533d2-127">.NET Framework Security</span></span>  
 <span data-ttu-id="533d2-128">La clé privée d'une paire de clés asymétriques ne doit jamais être stockée ni transférée en texte brut.</span><span class="sxs-lookup"><span data-stu-id="533d2-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="533d2-129">Pour plus d’informations sur les clés de chiffrement symétriques et asymétriques, consultez [génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="533d2-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="533d2-130">N'incorporez jamais une clé privée directement dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="533d2-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="533d2-131">Les clés incorporées peuvent être facilement lues à partir d’un assembly à l’aide d' [Ildasm. exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) ou en ouvrant l’assembly dans un éditeur de texte tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="533d2-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="533d2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="533d2-132">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="533d2-133">Comment : signer des documents XML avec des signatures numériques</span><span class="sxs-lookup"><span data-stu-id="533d2-133">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)
