---
title: 'Comment : stocker des clés asymétriques dans un conteneur de clé'
ms.date: 05/26/2020
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
ms.openlocfilehash: 36bae05fbfb35dc112e0c543c9a1a975a8fa8db5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143619"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="c7ee9-102">Stocker des clés asymétriques dans un conteneur de clé</span><span class="sxs-lookup"><span data-stu-id="c7ee9-102">Store asymmetric keys in a key container</span></span>

<span data-ttu-id="c7ee9-103">Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="c7ee9-104">Si vous avez besoin de stocker une clé privée, utilisez un conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-104">If you need to store a private key, use a key container.</span></span> <span data-ttu-id="c7ee9-105">Pour plus d’informations sur les conteneurs de clé, consultez [comprendre les conteneurs de clés RSA au niveau de l’ordinateur et au niveau de l’utilisateur](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c7ee9-105">For more information on key containers, see [Understanding machine-level and user-level RSA key containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="c7ee9-106">Créer une clé asymétrique et l’enregistrer dans un conteneur de clé</span><span class="sxs-lookup"><span data-stu-id="c7ee9-106">Create an asymmetric key and save it in a key container</span></span>

1. <span data-ttu-id="c7ee9-107">Créez une nouvelle instance d’une <xref:System.Security.Cryptography.CspParameters> classe et transmettez le nom auquel vous souhaitez appeler le conteneur de clé dans le <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> champ.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="c7ee9-108">Créez une nouvelle instance d’une classe qui dérive de la <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (généralement <xref:System.Security.Cryptography.RSACryptoServiceProvider> ou <xref:System.Security.Cryptography.DSACryptoServiceProvider> ) et transmettez l’objet créé précédemment `CspParameters` à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually <xref:System.Security.Cryptography.RSACryptoServiceProvider> or <xref:System.Security.Cryptography.DSACryptoServiceProvider>) and pass the previously created `CspParameters` object to its constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="c7ee9-109">La création et la récupération d’une clé asymétrique sont une opération.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-109">The creation and retrieval of an asymmetric key is one operation.</span></span> <span data-ttu-id="c7ee9-110">Si une clé n’est pas déjà dans le conteneur, elle est créée avant d’être retournée.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-110">If a key is not already in the container, it's created before being returned.</span></span>
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a><span data-ttu-id="c7ee9-111">Supprimer la clé du conteneur de clé</span><span class="sxs-lookup"><span data-stu-id="c7ee9-111">Delete the key from the key container</span></span>

1. <span data-ttu-id="c7ee9-112">Créez une nouvelle instance d’une `CspParameters` classe et transmettez le nom auquel vous souhaitez appeler le conteneur de clé dans le <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> champ.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-112">Create a new instance of a `CspParameters` class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="c7ee9-113">Créez une nouvelle instance d’une classe qui dérive de la <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (généralement `RSACryptoServiceProvider` ou `DSACryptoServiceProvider` ) et transmettez l’objet créé précédemment `CspParameters` à son constructeur.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-113">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually `RSACryptoServiceProvider` or `DSACryptoServiceProvider`) and pass the previously created `CspParameters` object to its constructor.</span></span>

1. <span data-ttu-id="c7ee9-114">Affectez à la <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> propriété ou de la classe qui dérive de la valeur `AsymmetricAlgorithm` `false` ( `False` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c7ee9-114">Set the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> or the <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> property of the class that derives from `AsymmetricAlgorithm` to `false` (`False` in Visual Basic).</span></span>

1. <span data-ttu-id="c7ee9-115">Appelez la `Clear` méthode de la classe qui dérive de `AsymmetricAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="c7ee9-115">Call the `Clear` method of the class that derives from `AsymmetricAlgorithm`.</span></span> <span data-ttu-id="c7ee9-116">Cette méthode libère toutes les ressources de la classe et efface le conteneur de clés.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-116">This method releases all resources of the class and clears the key container.</span></span>

## <a name="example"></a><span data-ttu-id="c7ee9-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7ee9-117">Example</span></span>

<span data-ttu-id="c7ee9-118">L'exemple suivant illustre comment créer une clé asymétrique, l'enregistrer dans un conteneur de clés, récupérer la clé ultérieurement et supprimer la clé du conteneur.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-118">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>

<span data-ttu-id="c7ee9-119">Notez que le code inclus dans la méthode `GenKey_SaveInContainer` est similaire à celui de la méthode `GetKeyFromContainer`.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-119">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span> <span data-ttu-id="c7ee9-120">Lorsque vous spécifiez un nom de conteneur de clé pour un <xref:System.Security.Cryptography.CspParameters> objet et que vous le transmettez à un <xref:System.Security.Cryptography.AsymmetricAlgorithm> objet dont la <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> propriété ou la propriété a la <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> valeur `true` , le comportement est le suivant :</span><span class="sxs-lookup"><span data-stu-id="c7ee9-120">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to `true`, the behavior is as follows:</span></span>

- <span data-ttu-id="c7ee9-121">S'il n'existe aucun conteneur de clés portant le nom spécifié, un conteneur est créé et la clé est conservée.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-121">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>
- <span data-ttu-id="c7ee9-122">Si un conteneur de clés portant le nom spécifié existe déjà, la clé incluse dans ce conteneur est automatiquement chargée dans l'objet <xref:System.Security.Cryptography.AsymmetricAlgorithm> actuel.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-122">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>

<span data-ttu-id="c7ee9-123">Par conséquent, le code de la `GenKey_SaveInContainer` méthode conserve la clé car il est exécuté en premier, tandis que le code de la `GetKeyFromContainer` méthode charge la clé car il est exécuté en second.</span><span class="sxs-lookup"><span data-stu-id="c7ee9-123">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it's run second.</span></span>

```vb
Imports System
Imports System.Security.Cryptography

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

    Private Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key added to container:  {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub GetKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key retrieved from container : {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container.
        ' Delete the key entry in the container.
        Dim rsa As New RSACryptoServiceProvider(parameters) With {
            .PersistKeyInCsp = False
        }

        ' Call Clear to release resources and delete the key from the container.
        rsa.Clear()

        Console.WriteLine("Key deleted.")
    End Sub
End Class
```

```csharp
using System;
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
        catch (CryptographicException e)
        {
            Console.WriteLine(e.Message);
        }
    }

    private static void GenKey_SaveInContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key added to container: \n  {rsa.ToXmlString(true)}");
    }

    private static void GetKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key retrieved from container : \n {rsa.ToXmlString(true)}");
    }

    private static void DeleteKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container.
        using var rsa = new RSACryptoServiceProvider(parameters)
        {
            // Delete the key entry in the container.
            PersistKeyInCsp = false
        };

        // Call Clear to release resources and delete the key from the container.
        rsa.Clear();

        Console.WriteLine("Key deleted.");
    }
}
```

<span data-ttu-id="c7ee9-124">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="c7ee9-124">The output is as follows:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c7ee9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7ee9-125">See also</span></span>

- [<span data-ttu-id="c7ee9-126">Génération de clés pour le chiffrement et le déchiffrement</span><span class="sxs-lookup"><span data-stu-id="c7ee9-126">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="c7ee9-127">Chiffrement des données</span><span class="sxs-lookup"><span data-stu-id="c7ee9-127">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="c7ee9-128">Déchiffrement des données</span><span class="sxs-lookup"><span data-stu-id="c7ee9-128">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="c7ee9-129">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="c7ee9-129">Cryptographic services</span></span>](cryptographic-services.md)
