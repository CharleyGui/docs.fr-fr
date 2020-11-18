---
title: 'Procédure : chiffrer des éléments XML avec des certificats X.509'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: 5007404c1e6e872c169ce7ce71425f14d20d3a25
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820187"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="97a79-102">Procédure : chiffrer des éléments XML avec des certificats X.509</span><span class="sxs-lookup"><span data-stu-id="97a79-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="97a79-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="97a79-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="97a79-104">Le chiffrement XML est une méthode normalisée qui permet d'échanger et de stocker des données XML chiffrées sans que celles-ci ne puissent être lues facilement.</span><span class="sxs-lookup"><span data-stu-id="97a79-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="97a79-105">Pour plus d’informations sur la norme de chiffrement XML, consultez la spécification World Wide Web Consortium (W3C) pour le chiffrement XML situé dans <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="97a79-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="97a79-106">Vous pouvez utiliser le chiffrement XML pour remplacer tout élément XML ou tout document comportant un élément <`EncryptedData`> qui contient des données XML chiffrées.</span><span class="sxs-lookup"><span data-stu-id="97a79-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="97a79-107">L'élément <`EncryptedData`> peut contenir des sous-éléments qui incluent des informations sur les clés et les processus utilisés pendant le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="97a79-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="97a79-108">Le chiffrement XML permet à un document de contenir plusieurs éléments chiffrés et permet à un élément d'être chiffré plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="97a79-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="97a79-109">L'exemple de code de cette procédure vous montre comment créer un élément <`EncryptedData`> avec plusieurs sous-éléments que vous pouvez utiliser ultérieurement pendant le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="97a79-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
<span data-ttu-id="97a79-110">Cet exemple chiffre un élément XML à l'aide de deux clés.</span><span class="sxs-lookup"><span data-stu-id="97a79-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="97a79-111">L’exemple récupère par programme un certificat et l’utilise pour chiffrer un élément XML à l’aide de la <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="97a79-111">The example programmatically retrieves a certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="97a79-112">En interne, la méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> crée une clé de session séparée et l'utilise pour chiffrer le document XML.</span><span class="sxs-lookup"><span data-stu-id="97a79-112">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="97a79-113">Cette méthode chiffre la clé de session et l'enregistre avec le code XML chiffré dans un nouvel élément <`EncryptedData`>.</span><span class="sxs-lookup"><span data-stu-id="97a79-113">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  

<span data-ttu-id="97a79-114">Pour déchiffrer l’élément XML, appelez la <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> méthode, qui récupère automatiquement le certificat X. 509 à partir du magasin et effectue le déchiffrement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="97a79-114">To decrypt the XML element, call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="97a79-115">Pour plus d’informations sur le déchiffrement d’un élément XML chiffré à l’aide de cette procédure, consultez [Comment : déchiffrer des éléments XML avec les certificats X.509](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="97a79-115">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
<span data-ttu-id="97a79-116">Cet exemple convient quand plusieurs applications doivent partager des données chiffrées ou quand une application doit enregistrer des données chiffrées entre chaque exécution.</span><span class="sxs-lookup"><span data-stu-id="97a79-116">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="97a79-117">Pour chiffrer un élément XML avec un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="97a79-117">To encrypt an XML element with an X.509 certificate</span></span>  

<span data-ttu-id="97a79-118">Pour exécuter cet exemple, vous devez créer un certificat de test et l’enregistrer dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="97a79-118">To run this example, you need to create a test certificate and save it in a certificate store.</span></span> <span data-ttu-id="97a79-119">Les instructions relatives à cette tâche sont fournies uniquement pour l' [outil de création de certificats Windows (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="97a79-119">Instructions for that task are provided only for the Windows [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span></span>

1. <span data-ttu-id="97a79-120">Utilisez [Makecert.exe](/windows/desktop/SecCrypto/makecert) pour générer un certificat X. 509 de test et le placer dans le magasin de l’utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="97a79-120">Use [Makecert.exe](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="97a79-121">Vous devez générer une clé d'échange et rendre cette clé exportable.</span><span class="sxs-lookup"><span data-stu-id="97a79-121">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="97a79-122">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="97a79-122">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="97a79-123">Créez un objet <xref:System.Security.Cryptography.X509Certificates.X509Store> et initialisez-le pour ouvrir le magasin de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="97a79-123">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="97a79-124">Ouvrez le magasin en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="97a79-124">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="97a79-125">Initialisez un <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> avec tous les certificats du magasin.</span><span class="sxs-lookup"><span data-stu-id="97a79-125">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="97a79-126">Énumérez les certificats du magasin et recherchez le certificat portant le nom approprié.</span><span class="sxs-lookup"><span data-stu-id="97a79-126">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="97a79-127">Dans cet exemple, le certificat se nomme `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="97a79-127">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="97a79-128">Quand vous avez trouvé le certificat, fermez le magasin.</span><span class="sxs-lookup"><span data-stu-id="97a79-128">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="97a79-129">Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.</span><span class="sxs-lookup"><span data-stu-id="97a79-129">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="97a79-130">L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à chiffrer.</span><span class="sxs-lookup"><span data-stu-id="97a79-130">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="97a79-131">Recherchez l'élément spécifié dans l'objet <xref:System.Xml.XmlDocument>, puis créez un objet <xref:System.Xml.XmlElement> pour représenter l'élément que vous voulez chiffrer.</span><span class="sxs-lookup"><span data-stu-id="97a79-131">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="97a79-132">Dans cet exemple, l'élément `"creditcard"` est chiffré.</span><span class="sxs-lookup"><span data-stu-id="97a79-132">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="97a79-133">Créez une instance de la classe <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez-la pour chiffrer l'élément spécifié à l'aide du certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="97a79-133">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="97a79-134">La méthode <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> retourne l'élément chiffré en tant qu'objet <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="97a79-134">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="97a79-135">Remplacez l'élément de l'objet <xref:System.Xml.XmlDocument> d'origine par l'élément <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="97a79-135">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="97a79-136">Enregistrez l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="97a79-136">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="97a79-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="97a79-137">Example</span></span>  
 <span data-ttu-id="97a79-138">Cet exemple suppose qu'un fichier nommé `"test.xml"` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="97a79-138">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="97a79-139">Il suppose également que `"test.xml"` contient un élément `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="97a79-139">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="97a79-140">Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="97a79-140">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="97a79-141">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="97a79-141">Compiling the Code</span></span>  
  
- <span data-ttu-id="97a79-142">Dans un projet qui cible .NET Framework, incluez une référence à `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="97a79-142">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="97a79-143">Dans un projet qui cible .NET Core ou .NET 5, installez le package NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="97a79-143">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="97a79-144">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="97a79-144">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="97a79-145">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="97a79-145">.NET Security</span></span>
  
<span data-ttu-id="97a79-146">Le certificat X.509 utilisé dans cet exemple sert à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="97a79-146">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="97a79-147">Les applications doivent utiliser un certificat X. 509 généré par une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="97a79-147">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a79-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97a79-148">See also</span></span>

- [<span data-ttu-id="97a79-149">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="97a79-149">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="97a79-150">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="97a79-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="97a79-151">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="97a79-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="97a79-152">Procédure : déchiffrer des éléments XML avec des certificats X.509</span><span class="sxs-lookup"><span data-stu-id="97a79-152">How to: Decrypt XML Elements with X.509 Certificates</span></span>](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="97a79-153">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="97a79-153">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
