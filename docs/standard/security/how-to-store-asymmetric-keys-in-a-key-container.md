---
title: 'Comment : stocker des clés asymétriques dans un conteneur de clé'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
ms.openlocfilehash: 6b703156b38f52513c86f7b2507ac6c185a9dd50
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155943"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="a634c-102">Comment : stocker des clés asymétriques dans un conteneur de clé</span><span class="sxs-lookup"><span data-stu-id="a634c-102">How to: Store Asymmetric Keys in a Key Container</span></span>
<span data-ttu-id="a634c-103">Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a634c-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="a634c-104">Si vous avez besoin de stocker une clé privée, vous devez utiliser un conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="a634c-104">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="a634c-105">Pour plus d’informations sur les conteneurs de clé, consultez [Présentation des conteneurs de clé RSA ordinateur et utilisateur](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a634c-105">For more information on key containers, see [Understanding Machine-Level and User-Level RSA Key Containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="a634c-106">Pour créer une clé asymétrique et l'enregistrer dans un conteneur de clés</span><span class="sxs-lookup"><span data-stu-id="a634c-106">To create an asymmetric key and save it in a key container</span></span>  
  
1. <span data-ttu-id="a634c-107">Créez une nouvelle instance d’une classe <xref:System.Security.Cryptography.CspParameters> et transmettez le nom que vous souhaitez appeler au conteneur de clé dans le champ <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a634c-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>  
  
2. <span data-ttu-id="a634c-108">Créez une nouvelle instance d’une classe qui dérive de la classe <xref:System.Security.Cryptography.AsymmetricAlgorithm> (généralement **RSACryptoServiceProvider** ou **DSACryptoServiceProvider**) et transmettez l’objet **CspParameters** créé précédemment à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="a634c-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
### <a name="to-delete-the-key-from-a-key-container"></a><span data-ttu-id="a634c-109">Pour supprimer la clé dans un conteneur de clés</span><span class="sxs-lookup"><span data-stu-id="a634c-109">To delete the key from a key container</span></span>  
  
1. <span data-ttu-id="a634c-110">Créez une nouvelle instance d’une classe **CspParameters** et passez le nom que vous souhaitez donner au conteneur de clé dans le champ **CspParameters.KeyContainerName**.</span><span class="sxs-lookup"><span data-stu-id="a634c-110">Create a new instance of a **CspParameters** class and pass the name that you want to call the key container to the **CspParameters.KeyContainerName** field.</span></span>  
  
2. <span data-ttu-id="a634c-111">Créez une nouvelle instance d’une classe qui dérive de la classe **AsymmetricAlgorithm** (habituellement **RSACryptoServiceProvider** ou **DSACryptoServiceProvider**) et passez l’objet **CspParameters** créé précédemment à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="a634c-111">Create a new instance of a class that derives from the **AsymmetricAlgorithm** class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
3. <span data-ttu-id="a634c-112">Affectez à la propriété **PersistKeyInCSP** de la classe qui dérive d’**AsymmetricAlgorithm** la valeur **false** (**False** dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a634c-112">Set the **PersistKeyInCSP** property of the class that derives from **AsymmetricAlgorithm** to **false** (**False** in Visual Basic).</span></span>  
  
4. <span data-ttu-id="a634c-113">Appelez la méthode **Clear** de la classe qui dérive d’**AsymmetricAlgorithm**.</span><span class="sxs-lookup"><span data-stu-id="a634c-113">Call the **Clear** method of the class that derives from **AsymmetricAlgorithm**.</span></span> <span data-ttu-id="a634c-114">Cette méthode libère toutes les ressources de la classe et efface le conteneur de clés.</span><span class="sxs-lookup"><span data-stu-id="a634c-114">This method releases all resources of the class and clears the key container.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a634c-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="a634c-115">Example</span></span>  
 <span data-ttu-id="a634c-116">L'exemple suivant illustre comment créer une clé asymétrique, l'enregistrer dans un conteneur de clés, récupérer la clé ultérieurement et supprimer la clé du conteneur.</span><span class="sxs-lookup"><span data-stu-id="a634c-116">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>  
  
 <span data-ttu-id="a634c-117">Notez que le code inclus dans la méthode `GenKey_SaveInContainer` est similaire à celui de la méthode `GetKeyFromContainer`.</span><span class="sxs-lookup"><span data-stu-id="a634c-117">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span>  <span data-ttu-id="a634c-118">Quand vous spécifiez un nom de conteneur de clés pour un objet <xref:System.Security.Cryptography.CspParameters> et le passez à un objet <xref:System.Security.Cryptography.AsymmetricAlgorithm> avec la propriété <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> ou la propriété <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> définie sur true, les événements suivants se produisent.</span><span class="sxs-lookup"><span data-stu-id="a634c-118">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to true, the following occurs.</span></span>  <span data-ttu-id="a634c-119">S'il n'existe aucun conteneur de clés portant le nom spécifié, un conteneur est créé et la clé est conservée.</span><span class="sxs-lookup"><span data-stu-id="a634c-119">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>  <span data-ttu-id="a634c-120">Si un conteneur de clés portant le nom spécifié existe déjà, la clé incluse dans ce conteneur est automatiquement chargée dans l'objet <xref:System.Security.Cryptography.AsymmetricAlgorithm> actuel.</span><span class="sxs-lookup"><span data-stu-id="a634c-120">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>  <span data-ttu-id="a634c-121">Par conséquent, le code inclus dans la méthode `GenKey_SaveInContainer` conserve la clé car il est exécuté en premier, tandis que le code inclus dans la méthode `GetKeyFromContainer` charge la clé car il est exécuté en second.</span><span class="sxs-lookup"><span data-stu-id="a634c-121">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it is run second.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```console  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a634c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a634c-122">See also</span></span>

- [<span data-ttu-id="a634c-123">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="a634c-123">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="a634c-124">Chiffrement de données</span><span class="sxs-lookup"><span data-stu-id="a634c-124">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="a634c-125">Déchiffrement de données</span><span class="sxs-lookup"><span data-stu-id="a634c-125">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="a634c-126">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a634c-126">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
