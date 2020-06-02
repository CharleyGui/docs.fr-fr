---
title: 'Comment : déchiffrer des éléments XML avec des clés symétriques'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: bb34332d345ee7bcb9037dc7bdf0deebbe70c3c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277425"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="10e70-102">Comment : déchiffrer des éléments XML avec des clés symétriques</span><span class="sxs-lookup"><span data-stu-id="10e70-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="10e70-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="10e70-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="10e70-104">Le chiffrement XML vous permet de stocker et de transporter du code XML sensible, en empêchant qu'il soit facilement lu.</span><span class="sxs-lookup"><span data-stu-id="10e70-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="10e70-105">Cet exemple de code déchiffre un élément XML à l'aide de l'algorithme AES (Advanced Encryption Standard), également appelé Rijndael.</span><span class="sxs-lookup"><span data-stu-id="10e70-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="10e70-106">Pour plus d’informations sur le chiffrement d’un élément XML à l’aide de cette procédure, consultez [Comment : chiffrer des éléments XML avec des clés symétriques](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="10e70-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="10e70-107">Quand vous utilisez un algorithme symétrique comme AES pour chiffrer des données XML, vous devez utiliser la même clé pour chiffrer et déchiffrer les données XML.</span><span class="sxs-lookup"><span data-stu-id="10e70-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="10e70-108">L'exemple de cette procédure suppose que le code XML a été chiffré à l'aide de la même clé, et que l'auteur du chiffrement et l'auteur du déchiffrement s'accordent sur l'algorithme et la clé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="10e70-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="10e70-109">Dans cet exemple, la clé AES n'est ni stockée ni chiffrée dans le code XML chiffré.</span><span class="sxs-lookup"><span data-stu-id="10e70-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="10e70-110">Cet exemple convient aux situations où une seule application doit chiffrer des données à l'aide d'une clé de session stockée en mémoire ou à l'aide d'une clé de chiffrement forte dérivée d'un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="10e70-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="10e70-111">Dans les situations où plusieurs applications doivent partager des données XML chiffrées, envisagez d'utiliser une méthode de chiffrement basée sur un algorithme asymétrique ou sur un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="10e70-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="10e70-112">Pour déchiffrer un élément XML avec une clé symétrique</span><span class="sxs-lookup"><span data-stu-id="10e70-112">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="10e70-113">Chiffrez un élément XML avec la clé générée précédemment à l’aide des techniques décrites dans [Comment : chiffrer des éléments XML avec des clés symétriques](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="10e70-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="10e70-114">Recherchez l' `EncryptedData` élément <> (défini par la norme de chiffrement XML) dans un <xref:System.Xml.XmlDocument> objet qui contient le code XML chiffré et créez un nouvel <xref:System.Xml.XmlElement> objet pour représenter cet élément.</span><span class="sxs-lookup"><span data-stu-id="10e70-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="10e70-115">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedData> en chargeant les données XML brutes à partir de l'objet <xref:System.Xml.XmlElement> créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="10e70-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="10e70-116">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez-le pour déchiffrer les données XML à l'aide de la même clé que celle utilisée pour le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="10e70-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="10e70-117">Remplacez l'élément chiffré par l'élément de texte brut dernièrement déchiffré dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="10e70-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="10e70-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="10e70-118">Example</span></span>  
 <span data-ttu-id="10e70-119">Cet exemple suppose qu'un fichier nommé `"test.xml"` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="10e70-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="10e70-120">Il suppose également que `"test.xml"` contient un élément `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="10e70-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="10e70-121">Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="10e70-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10e70-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="10e70-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="10e70-123">Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="10e70-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="10e70-124">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="10e70-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="10e70-125">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="10e70-125">.NET Framework Security</span></span>  
 <span data-ttu-id="10e70-126">Ne stockez jamais une clé de chiffrement en texte brut et ne transférez jamais une clé d'un ordinateur à l'autre en texte brut.</span><span class="sxs-lookup"><span data-stu-id="10e70-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="10e70-127">Quand vous avez terminé d'utiliser une clé de chiffrement symétrique, effacez-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.</span><span class="sxs-lookup"><span data-stu-id="10e70-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e70-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10e70-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="10e70-129">Comment : chiffrer des éléments XML avec des clés symétriques</span><span class="sxs-lookup"><span data-stu-id="10e70-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](how-to-encrypt-xml-elements-with-symmetric-keys.md)
