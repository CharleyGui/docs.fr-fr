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
ms.openlocfilehash: 29fe7c229664b08c9e1563413525818f2e883198
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729341"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="a3d22-102">Procédure : chiffrer des éléments XML avec des clés asymétriques</span><span class="sxs-lookup"><span data-stu-id="a3d22-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="a3d22-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="a3d22-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="a3d22-104">Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.</span><span class="sxs-lookup"><span data-stu-id="a3d22-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="a3d22-105">Pour plus d’informations sur la norme de chiffrement XML, consultez la spécification World Wide Web Consortium (W3C) pour le chiffrement XML situé dans <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="a3d22-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="a3d22-106">Vous pouvez utiliser le chiffrement XML pour remplacer tout élément XML ou tout document comportant un élément <`EncryptedData`> qui contient des données XML chiffrées.</span><span class="sxs-lookup"><span data-stu-id="a3d22-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="a3d22-107">L' `EncryptedData` élément <> peut également contenir des sous-éléments qui incluent des informations sur les clés et les processus utilisés pendant le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a3d22-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="a3d22-108">Le chiffrement XML permet à un document de contenir plusieurs éléments chiffrés et permet à un élément d'être chiffré plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="a3d22-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="a3d22-109">L’exemple de code de cette procédure montre comment créer un `EncryptedData` élément <> avec plusieurs autres sous-éléments que vous pouvez utiliser ultérieurement pendant le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="a3d22-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="a3d22-110">Cet exemple chiffre un élément XML à l'aide de deux clés.</span><span class="sxs-lookup"><span data-stu-id="a3d22-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="a3d22-111">Il génère une paire de clés publique/privée RSA et l'enregistre dans un conteneur de clé sécurisé.</span><span class="sxs-lookup"><span data-stu-id="a3d22-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="a3d22-112">L’exemple crée ensuite une clé de session distincte à l’aide de l’algorithme Advanced Encryption Standard (AES).</span><span class="sxs-lookup"><span data-stu-id="a3d22-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm.</span></span>  <span data-ttu-id="a3d22-113">L'exemple utilise la clé de session AES pour chiffrer le document XML, puis utilise la clé publique RSA pour chiffrer la clé de session AES.</span><span class="sxs-lookup"><span data-stu-id="a3d22-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="a3d22-114">Enfin, l’exemple enregistre la clé de session AES chiffrée et les données XML chiffrées dans le document XML au sein d’un nouvel `EncryptedData` élément <>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="a3d22-115">Pour déchiffrer l'élément XML, vous devez récupérer la clé privée RSA du conteneur de clé, l'utiliser pour déchiffrer la clé de session et ensuite utiliser la clé de session pour déchiffrer le document.</span><span class="sxs-lookup"><span data-stu-id="a3d22-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="a3d22-116">Pour plus d’informations sur le déchiffrement d’un élément XML chiffré à l’aide de cette procédure, consultez [Comment : déchiffrer des éléments XML avec des clés asymétriques](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="a3d22-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="a3d22-117">Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.</span><span class="sxs-lookup"><span data-stu-id="a3d22-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="a3d22-118">Pour chiffrer un élément XML avec une clé asymétrique</span><span class="sxs-lookup"><span data-stu-id="a3d22-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="a3d22-119">Créez un objet <xref:System.Security.Cryptography.CspParameters> et spécifiez le nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="a3d22-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="a3d22-120">Générez une clé symétrique à l'aide de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="a3d22-121">La clé est automatiquement enregistrée dans le conteneur de clé quand vous passez l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="a3d22-122">Cette clé sera utilisée pour chiffrer la clé de session AES et peut être récupérée ultérieurement pour la déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="a3d22-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="a3d22-123">Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.</span><span class="sxs-lookup"><span data-stu-id="a3d22-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="a3d22-124">L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à chiffrer.</span><span class="sxs-lookup"><span data-stu-id="a3d22-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="a3d22-125">Recherchez l'élément spécifié dans l'objet <xref:System.Xml.XmlDocument>, puis créez un objet <xref:System.Xml.XmlElement> pour représenter l'élément que vous voulez chiffrer.</span><span class="sxs-lookup"><span data-stu-id="a3d22-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="a3d22-126">Dans cet exemple, l'élément `"creditcard"` est chiffré.</span><span class="sxs-lookup"><span data-stu-id="a3d22-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="a3d22-127">Créez une clé de session en utilisant la classe <xref:System.Security.Cryptography.Aes>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-127">Create a new session key using the <xref:System.Security.Cryptography.Aes> class.</span></span>  <span data-ttu-id="a3d22-128">Cette clé chiffrera l'élément XML, puis sera chiffrée et placée dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="a3d22-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="a3d22-129">Créez une instance de la classe <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez-la pour chiffrer l'élément spécifié à l'aide de la clé de session.</span><span class="sxs-lookup"><span data-stu-id="a3d22-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="a3d22-130">La méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> retourne l'élément chiffré en tant que tableau d'octets chiffrés.</span><span class="sxs-lookup"><span data-stu-id="a3d22-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="a3d22-131">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedData> et ajoutez-lui l'identificateur d'URL de l'élément XML chiffré.</span><span class="sxs-lookup"><span data-stu-id="a3d22-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="a3d22-132">Cet identificateur d'URL informe la partie chargée du déchiffrement que le code XML contient un élément chiffré.</span><span class="sxs-lookup"><span data-stu-id="a3d22-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="a3d22-133">Vous pouvez utiliser le champ <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pour spécifier l'identificateur d'URL.</span><span class="sxs-lookup"><span data-stu-id="a3d22-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="a3d22-134">L’élément XML en texte brut sera remplacé par un `EncryptedData` élément <> encapsulé par cet <xref:System.Security.Cryptography.Xml.EncryptedData> objet.</span><span class="sxs-lookup"><span data-stu-id="a3d22-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="a3d22-135">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptionMethod> qui sera initialisé vers l'identificateur d'URL de l'algorithme de chiffrement utilisé pour générer la clé de session.</span><span class="sxs-lookup"><span data-stu-id="a3d22-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="a3d22-136">Passez l'objet <xref:System.Security.Cryptography.Xml.EncryptionMethod> à la propriété <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="a3d22-137">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedKey> devant contenir la clé de session chiffrée.</span><span class="sxs-lookup"><span data-stu-id="a3d22-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="a3d22-138">Chiffrez la clé de session, ajoutez-la à l'objet <xref:System.Security.Cryptography.Xml.EncryptedKey>, puis entrez un nom de clé de session et une URL de d'identificateur de clé.</span><span class="sxs-lookup"><span data-stu-id="a3d22-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="a3d22-139">Créez un objet <xref:System.Security.Cryptography.Xml.DataReference> qui mappe les données chiffrées à une clé de session particulière.</span><span class="sxs-lookup"><span data-stu-id="a3d22-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="a3d22-140">Cette étape facultative vous permet de spécifier facilement que plusieurs parties d'un document XML ont été chiffrées par une même clé.</span><span class="sxs-lookup"><span data-stu-id="a3d22-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="a3d22-141">Ajoutez la clé chiffrée pour l'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="a3d22-142">Créez un objet <xref:System.Security.Cryptography.Xml.KeyInfo> pour spécifier le nom de la clé RSA.</span><span class="sxs-lookup"><span data-stu-id="a3d22-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="a3d22-143">Ajoutez-le à l'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="a3d22-144">Cela permet à la partie chargée du déchiffrement de trouver la clé asymétrique à utiliser pour le déchiffrement de la clé de session.</span><span class="sxs-lookup"><span data-stu-id="a3d22-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="a3d22-145">Ajoutez les données d'élément chiffrées à l'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="a3d22-146">Remplacez l'élément de l'objet <xref:System.Xml.XmlDocument> d'origine par l'élément <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="a3d22-147">Enregistrez l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="a3d22-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3d22-148">Example</span></span>  

 <span data-ttu-id="a3d22-149">Cet exemple suppose qu'un fichier nommé `"test.xml"` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="a3d22-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="a3d22-150">Il suppose également que `"test.xml"` contient un élément `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="a3d22-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="a3d22-151">Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="a3d22-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a3d22-152">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a3d22-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="a3d22-153">Dans un projet qui cible .NET Framework, incluez une référence à `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="a3d22-153">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="a3d22-154">Dans un projet qui cible .NET Core ou .NET 5, installez le package NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="a3d22-154">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="a3d22-155">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="a3d22-155">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="a3d22-156">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="a3d22-156">.NET Security</span></span>

<span data-ttu-id="a3d22-157">Ne stockez jamais une clé de chiffrement symétrique en texte brut et ne transférez jamais une clé symétrique d'un ordinateur à l'autre en texte brut.</span><span class="sxs-lookup"><span data-stu-id="a3d22-157">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="a3d22-158">De plus, la clé privée d'une paire de clés asymétriques ne doit jamais être stockée ni transférée en texte brut.</span><span class="sxs-lookup"><span data-stu-id="a3d22-158">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="a3d22-159">Pour plus d’informations sur les clés de chiffrement symétriques et asymétriques, consultez [génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="a3d22-159">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="a3d22-160">N'incorporez jamais une clé directement dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="a3d22-160">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="a3d22-161">Les clés incorporées peuvent être facilement lues à partir d’un assembly à l’aide de l' [Ildasm.exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) ou en ouvrant l’assembly dans un éditeur de texte tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="a3d22-161">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
<span data-ttu-id="a3d22-162">Quand vous avez terminé d'utiliser une clé de chiffrement, effacez-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.</span><span class="sxs-lookup"><span data-stu-id="a3d22-162">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="a3d22-163">Les clés de chiffrement peuvent parfois être lues à partir de la mémoire par un débogueur ou à partir d'un disque dur si l'emplacement de mémoire est paginé sur le disque.</span><span class="sxs-lookup"><span data-stu-id="a3d22-163">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d22-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3d22-164">See also</span></span>

- [<span data-ttu-id="a3d22-165">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a3d22-165">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="a3d22-166">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a3d22-166">Cryptographic Services</span></span>](cryptographic-services.md)
- <span data-ttu-id="a3d22-167">[Chiffrement multiplateforme](cross-platform-cryptography.md)- <xref:System.Security.Cryptography.Xml></span><span class="sxs-lookup"><span data-stu-id="a3d22-167">[Cross-Platform Cryptography](cross-platform-cryptography.md)- <xref:System.Security.Cryptography.Xml></span></span>
- [<span data-ttu-id="a3d22-168">Comment : déchiffrer des éléments XML avec des clés asymétriques</span><span class="sxs-lookup"><span data-stu-id="a3d22-168">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](how-to-decrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="a3d22-169">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a3d22-169">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
