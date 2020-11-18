---
title: 'Procédure : déchiffrer des éléments XML avec des clés asymétriques'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 0456c89987b37840daa1c84342528d11c6da73a4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822228"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="f266f-102">Procédure : déchiffrer des éléments XML avec des clés asymétriques</span><span class="sxs-lookup"><span data-stu-id="f266f-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="f266f-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer et déchiffrer un élément d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="f266f-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="f266f-104">Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.</span><span class="sxs-lookup"><span data-stu-id="f266f-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="f266f-105">Pour plus d’informations sur la norme de chiffrement XML, consultez la recommandation du W3C sur la [syntaxe et World Wide Web Consortium le traitement des signatures XML](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="f266f-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="f266f-106">Le code de cet article s’applique à Windows.</span><span class="sxs-lookup"><span data-stu-id="f266f-106">The code in this article applies to Windows.</span></span>

<span data-ttu-id="f266f-107">L’exemple de cette procédure déchiffre un élément XML qui a été chiffré à l’aide des méthodes décrites dans [Comment : chiffrer des éléments XML avec des clés asymétriques](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="f266f-107">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="f266f-108">Il recherche une <`EncryptedData` élément>, déchiffre l’élément, puis remplace l’élément par l’élément XML en texte brut d’origine.</span><span class="sxs-lookup"><span data-stu-id="f266f-108">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="f266f-109">Cet exemple déchiffre un élément XML à l'aide de deux clés.</span><span class="sxs-lookup"><span data-stu-id="f266f-109">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="f266f-110">Il récupère une clé privée RSA générée précédemment à partir d’un conteneur de clé, puis utilise la clé RSA pour déchiffrer une clé de session stockée dans l' `EncryptedKey` élément <> de l' `EncryptedData` élément> <.</span><span class="sxs-lookup"><span data-stu-id="f266f-110">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="f266f-111">L'exemple utilise ensuite la clé de session pour déchiffrer l'élément XML.</span><span class="sxs-lookup"><span data-stu-id="f266f-111">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="f266f-112">Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.</span><span class="sxs-lookup"><span data-stu-id="f266f-112">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="f266f-113">Pour déchiffrer un élément XML avec une clé asymétrique</span><span class="sxs-lookup"><span data-stu-id="f266f-113">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="f266f-114">Créez un objet <xref:System.Security.Cryptography.CspParameters> et spécifiez le nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="f266f-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="f266f-115">Récupérez une clé asymétrique générée précédemment à partir du conteneur à l'aide de l'objet <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="f266f-115">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="f266f-116">La clé est automatiquement récupérée depuis le conteneur de clé quand vous passez l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="f266f-116">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="f266f-117">Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedXml> pour déchiffrer le document.</span><span class="sxs-lookup"><span data-stu-id="f266f-117">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="f266f-118">Ajoutez un mappage nom/clé pour associer la clé RSA à l'élément dans le document qui doit être déchiffré.</span><span class="sxs-lookup"><span data-stu-id="f266f-118">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="f266f-119">Vous devez utiliser le même nom de clé que celui que vous avez utilisé quand vous avez chiffré le document.</span><span class="sxs-lookup"><span data-stu-id="f266f-119">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="f266f-120">Notez que ce nom est différent du nom utilisé pour identifier la clé dans le conteneur de clé spécifié à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="f266f-120">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="f266f-121">Appelez la <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> méthode pour déchiffrer l' `EncryptedData` élément <>.</span><span class="sxs-lookup"><span data-stu-id="f266f-121">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="f266f-122">Cette méthode utilise la clé RSA pour déchiffrer la clé de session et utilise automatiquement la clé de session pour déchiffrer l'élément XML.</span><span class="sxs-lookup"><span data-stu-id="f266f-122">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="f266f-123">Il remplace également automatiquement l' `EncryptedData` élément <> par le texte brut d’origine.</span><span class="sxs-lookup"><span data-stu-id="f266f-123">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="f266f-124">Enregistrez le document XML</span><span class="sxs-lookup"><span data-stu-id="f266f-124">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="f266f-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="f266f-125">Example</span></span>

<span data-ttu-id="f266f-126">Cet exemple suppose qu'un fichier nommé `test.xml` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="f266f-126">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="f266f-127">Il suppose également que `test.xml` contient un élément XML qui a été chiffré à l’aide des techniques décrites dans [Comment : chiffrer des éléments XML avec des clés asymétriques](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="f266f-127">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f266f-128">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f266f-128">Compiling the Code</span></span>  
  
- <span data-ttu-id="f266f-129">Dans un projet qui cible .NET Framework, incluez une référence à `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="f266f-129">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="f266f-130">Dans un projet qui cible .NET Core ou .NET 5, installez le package NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="f266f-130">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="f266f-131">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="f266f-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="f266f-132">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="f266f-132">.NET Security</span></span>  

<span data-ttu-id="f266f-133">Ne stockez jamais une clé de chiffrement symétrique en texte brut et ne transférez jamais une clé symétrique d'un ordinateur à l'autre en texte brut.</span><span class="sxs-lookup"><span data-stu-id="f266f-133">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="f266f-134">De plus, la clé privée d'une paire de clés asymétriques ne doit jamais être stockée ni transférée en texte brut.</span><span class="sxs-lookup"><span data-stu-id="f266f-134">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="f266f-135">Pour plus d’informations sur les clés de chiffrement symétriques et asymétriques, consultez [génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="f266f-135">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="f266f-136">N'incorporez jamais une clé directement dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="f266f-136">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="f266f-137">Les clés incorporées peuvent être facilement lues à partir d’un assembly à l’aide d' [Ildasm.exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) ou en ouvrant l’assembly dans un éditeur de texte tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="f266f-137">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="f266f-138">Quand vous avez terminé d'utiliser une clé de chiffrement, effacez-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.</span><span class="sxs-lookup"><span data-stu-id="f266f-138">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="f266f-139">Les clés de chiffrement peuvent parfois être lues à partir de la mémoire par un débogueur ou à partir d'un disque dur si l'emplacement de mémoire est paginé sur le disque.</span><span class="sxs-lookup"><span data-stu-id="f266f-139">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f266f-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f266f-140">See also</span></span>

- [<span data-ttu-id="f266f-141">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="f266f-141">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="f266f-142">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="f266f-142">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="f266f-143">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="f266f-143">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="f266f-144">Comment : chiffrer des éléments XML avec des clés asymétriques</span><span class="sxs-lookup"><span data-stu-id="f266f-144">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="f266f-145">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f266f-145">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
