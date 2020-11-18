---
title: 'Procédure : déchiffrer des éléments XML avec des clés symétriques'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: de53cc8ef728ddc40bc8e1138a1d649e5c3e600b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820304"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="6e214-102">Procédure : déchiffrer des éléments XML avec des clés symétriques</span><span class="sxs-lookup"><span data-stu-id="6e214-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="6e214-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="6e214-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="6e214-104">Le chiffrement XML vous permet de stocker et de transporter du code XML sensible, en empêchant qu'il soit facilement lu.</span><span class="sxs-lookup"><span data-stu-id="6e214-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="6e214-105">Cet exemple de code déchiffre un élément XML à l’aide de l’algorithme Advanced Encryption Standard (AES).</span><span class="sxs-lookup"><span data-stu-id="6e214-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>
  
 <span data-ttu-id="6e214-106">Pour plus d’informations sur le chiffrement d’un élément XML à l’aide de cette procédure, consultez [Comment : chiffrer des éléments XML avec des clés symétriques](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="6e214-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="6e214-107">Quand vous utilisez un algorithme symétrique comme AES pour chiffrer des données XML, vous devez utiliser la même clé pour chiffrer et déchiffrer les données XML.</span><span class="sxs-lookup"><span data-stu-id="6e214-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="6e214-108">L'exemple de cette procédure suppose que le code XML a été chiffré à l'aide de la même clé, et que l'auteur du chiffrement et l'auteur du déchiffrement s'accordent sur l'algorithme et la clé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6e214-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="6e214-109">Dans cet exemple, la clé AES n'est ni stockée ni chiffrée dans le code XML chiffré.</span><span class="sxs-lookup"><span data-stu-id="6e214-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="6e214-110">Cet exemple convient aux situations où une seule application doit chiffrer des données à l'aide d'une clé de session stockée en mémoire ou à l'aide d'une clé de chiffrement forte dérivée d'un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6e214-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="6e214-111">Dans les situations où plusieurs applications doivent partager des données XML chiffrées, envisagez d'utiliser une méthode de chiffrement basée sur un algorithme asymétrique ou sur un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="6e214-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="6e214-112">Pour déchiffrer un élément XML avec une clé symétrique</span><span class="sxs-lookup"><span data-stu-id="6e214-112">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="6e214-113">Chiffrez un élément XML avec la clé générée précédemment à l’aide des techniques décrites dans [Comment : chiffrer des éléments XML avec des clés symétriques](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="6e214-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="6e214-114">Recherchez l' `EncryptedData` élément <> (défini par la norme de chiffrement XML) dans un <xref:System.Xml.XmlDocument> objet qui contient le code XML chiffré et créez un nouvel <xref:System.Xml.XmlElement> objet pour représenter cet élément.</span><span class="sxs-lookup"><span data-stu-id="6e214-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="6e214-115">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedData> en chargeant les données XML brutes à partir de l'objet <xref:System.Xml.XmlElement> créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="6e214-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="6e214-116">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez-le pour déchiffrer les données XML à l'aide de la même clé que celle utilisée pour le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6e214-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="6e214-117">Remplacez l'élément chiffré par l'élément de texte brut dernièrement déchiffré dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="6e214-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="6e214-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e214-118">Example</span></span>  
 <span data-ttu-id="6e214-119">Cet exemple suppose qu'un fichier nommé `"test.xml"` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="6e214-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="6e214-120">Il suppose également que `"test.xml"` contient un élément `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="6e214-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="6e214-121">Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="6e214-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="6e214-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6e214-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="6e214-123">Dans un projet qui cible .NET Framework, incluez une référence à `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="6e214-123">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="6e214-124">Dans un projet qui cible .NET Core ou .NET 5, installez le package NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="6e214-124">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="6e214-125">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="6e214-125">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="6e214-126">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="6e214-126">.NET Security</span></span>
  
<span data-ttu-id="6e214-127">Ne stockez jamais une clé de chiffrement en texte brut et ne transférez jamais une clé d'un ordinateur à l'autre en texte brut.</span><span class="sxs-lookup"><span data-stu-id="6e214-127">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
<span data-ttu-id="6e214-128">Quand vous avez terminé d'utiliser une clé de chiffrement symétrique, effacez-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.</span><span class="sxs-lookup"><span data-stu-id="6e214-128">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e214-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e214-129">See also</span></span>

- [<span data-ttu-id="6e214-130">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6e214-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="6e214-131">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6e214-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="6e214-132">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="6e214-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="6e214-133">Procédure : chiffrer des éléments XML avec des clés symétriques</span><span class="sxs-lookup"><span data-stu-id="6e214-133">How to: Encrypt XML Elements with Symmetric Keys</span></span>](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="6e214-134">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6e214-134">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
