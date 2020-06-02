---
title: 'Comment : chiffrer des éléments XML avec des clés symétriques'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: 1ad75b7f36130a9f3acad97f724406650a7fdb68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277321"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="5df1d-102">Comment : chiffrer des éléments XML avec des clés symétriques</span><span class="sxs-lookup"><span data-stu-id="5df1d-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="5df1d-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="5df1d-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="5df1d-104">Le chiffrement XML vous permet de stocker et de transporter du code XML sensible, en empêchant qu'il soit facilement lu.</span><span class="sxs-lookup"><span data-stu-id="5df1d-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="5df1d-105">Cette procédure chiffre un élément XML à l’aide de l’algorithme Advanced Encryption Standard (AES), également appelé Rijndael.</span><span class="sxs-lookup"><span data-stu-id="5df1d-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="5df1d-106">Pour plus d’informations sur le déchiffrement d’un élément XML chiffré à l’aide de cette procédure, consultez [Comment : déchiffrer des éléments XML avec des clés symétriques](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="5df1d-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="5df1d-107">Quand vous utilisez un algorithme symétrique comme AES pour chiffrer des données XML, vous devez utiliser la même clé pour chiffrer et déchiffrer les données XML.</span><span class="sxs-lookup"><span data-stu-id="5df1d-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="5df1d-108">L'exemple de cette procédure suppose que le code XML chiffré sera déchiffré à l'aide de la même clé, et que les parties chargées du chiffrement et du déchiffrement se sont mises d'accord sur l'algorithme et la clé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5df1d-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="5df1d-109">Dans cet exemple, la clé AES n'est ni stockée ni chiffrée dans le code XML chiffré.</span><span class="sxs-lookup"><span data-stu-id="5df1d-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="5df1d-110">Cet exemple convient aux situations où une seule application doit chiffrer des données à l'aide d'une clé de session stockée en mémoire ou à l'aide d'une clé de chiffrement forte dérivée d'un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5df1d-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="5df1d-111">Dans les situations où plusieurs applications doivent partager des données XML chiffrées, envisagez d'utiliser une méthode de chiffrement basée sur un algorithme asymétrique ou sur un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="5df1d-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="5df1d-112">Pour chiffrer un élément XML avec une clé symétrique</span><span class="sxs-lookup"><span data-stu-id="5df1d-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="5df1d-113">Générez une clé symétrique à l'aide de la classe <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="5df1d-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="5df1d-114">Cette clé sera utilisée pour chiffrer l'élément XML.</span><span class="sxs-lookup"><span data-stu-id="5df1d-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="5df1d-115">Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.</span><span class="sxs-lookup"><span data-stu-id="5df1d-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="5df1d-116">L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à chiffrer.</span><span class="sxs-lookup"><span data-stu-id="5df1d-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="5df1d-117">Recherchez l'élément spécifié dans l'objet <xref:System.Xml.XmlDocument>, puis créez un objet <xref:System.Xml.XmlElement> pour représenter l'élément que vous voulez chiffrer.</span><span class="sxs-lookup"><span data-stu-id="5df1d-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="5df1d-118">Dans cet exemple, l'élément `"creditcard"` est chiffré.</span><span class="sxs-lookup"><span data-stu-id="5df1d-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="5df1d-119">Créez une instance de la classe <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez-la pour chiffrer <xref:System.Xml.XmlElement> avec la clé symétrique.</span><span class="sxs-lookup"><span data-stu-id="5df1d-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="5df1d-120">La méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> retourne l'élément chiffré en tant que tableau d'octets chiffrés.</span><span class="sxs-lookup"><span data-stu-id="5df1d-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="5df1d-121">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedData> et ajoutez-lui l'identificateur d'URL de l'élément XML chiffré.</span><span class="sxs-lookup"><span data-stu-id="5df1d-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="5df1d-122">Cet identificateur d'URL informe la partie chargée du déchiffrement que le code XML contient un élément chiffré.</span><span class="sxs-lookup"><span data-stu-id="5df1d-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="5df1d-123">Vous pouvez utiliser le champ <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pour spécifier l'identificateur d'URL.</span><span class="sxs-lookup"><span data-stu-id="5df1d-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="5df1d-124">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptionMethod> qui sera initialisé vers l'identificateur d'URL de l'algorithme de chiffrement utilisé pour générer la clé.</span><span class="sxs-lookup"><span data-stu-id="5df1d-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="5df1d-125">Passez l'objet <xref:System.Security.Cryptography.Xml.EncryptionMethod> à la propriété <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.</span><span class="sxs-lookup"><span data-stu-id="5df1d-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="5df1d-126">Ajoutez les données d'élément chiffrées à l'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="5df1d-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="5df1d-127">Remplacez l'élément de l'objet <xref:System.Xml.XmlDocument> d'origine par l'élément <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="5df1d-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="5df1d-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="5df1d-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="5df1d-129">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5df1d-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="5df1d-130">Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="5df1d-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="5df1d-131">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="5df1d-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5df1d-132">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5df1d-132">.NET Framework Security</span></span>  
 <span data-ttu-id="5df1d-133">Ne stockez jamais une clé de chiffrement en texte brut et ne transférez jamais une clé d'un ordinateur à l'autre en texte brut.</span><span class="sxs-lookup"><span data-stu-id="5df1d-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="5df1d-134">Vous devez utiliser un conteneur de clé sécurisé pour stocker les clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="5df1d-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="5df1d-135">Quand vous avez terminé d'utiliser une clé de chiffrement, effacez-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.</span><span class="sxs-lookup"><span data-stu-id="5df1d-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df1d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5df1d-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="5df1d-137">Comment : déchiffrer des éléments XML avec des clés symétriques</span><span class="sxs-lookup"><span data-stu-id="5df1d-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](how-to-decrypt-xml-elements-with-symmetric-keys.md)
