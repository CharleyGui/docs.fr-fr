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
# <a name="store-asymmetric-keys-in-a-key-container"></a>Stocker des clés asymétriques dans un conteneur de clé

Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local. Si vous avez besoin de stocker une clé privée, utilisez un conteneur de clé. Pour plus d’informations sur les conteneurs de clé, consultez [comprendre les conteneurs de clés RSA au niveau de l’ordinateur et au niveau de l’utilisateur](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Créer une clé asymétrique et l’enregistrer dans un conteneur de clé

1. Créez une nouvelle instance d’une <xref:System.Security.Cryptography.CspParameters> classe et transmettez le nom auquel vous souhaitez appeler le conteneur de clé dans le <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> champ.

1. Créez une nouvelle instance d’une classe qui dérive de la <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (généralement <xref:System.Security.Cryptography.RSACryptoServiceProvider> ou <xref:System.Security.Cryptography.DSACryptoServiceProvider> ) et transmettez l’objet créé précédemment `CspParameters` à son constructeur.

> [!NOTE]
> La création et la récupération d’une clé asymétrique sont une opération. Si une clé n’est pas déjà dans le conteneur, elle est créée avant d’être retournée.
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a>Supprimer la clé du conteneur de clé

1. Créez une nouvelle instance d’une `CspParameters` classe et transmettez le nom auquel vous souhaitez appeler le conteneur de clé dans le <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> champ.

1. Créez une nouvelle instance d’une classe qui dérive de la <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (généralement `RSACryptoServiceProvider` ou `DSACryptoServiceProvider` ) et transmettez l’objet créé précédemment `CspParameters` à son constructeur.

1. Affectez à la <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> propriété ou de la classe qui dérive de la valeur `AsymmetricAlgorithm` `false` ( `False` en Visual Basic).

1. Appelez la `Clear` méthode de la classe qui dérive de `AsymmetricAlgorithm` . Cette méthode libère toutes les ressources de la classe et efface le conteneur de clés.

## <a name="example"></a>Exemple

L'exemple suivant illustre comment créer une clé asymétrique, l'enregistrer dans un conteneur de clés, récupérer la clé ultérieurement et supprimer la clé du conteneur.

Notez que le code inclus dans la méthode `GenKey_SaveInContainer` est similaire à celui de la méthode `GetKeyFromContainer`. Lorsque vous spécifiez un nom de conteneur de clé pour un <xref:System.Security.Cryptography.CspParameters> objet et que vous le transmettez à un <xref:System.Security.Cryptography.AsymmetricAlgorithm> objet dont la <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> propriété ou la propriété a la <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> valeur `true` , le comportement est le suivant :

- S'il n'existe aucun conteneur de clés portant le nom spécifié, un conteneur est créé et la clé est conservée.
- Si un conteneur de clés portant le nom spécifié existe déjà, la clé incluse dans ce conteneur est automatiquement chargée dans l'objet <xref:System.Security.Cryptography.AsymmetricAlgorithm> actuel.

Par conséquent, le code de la `GenKey_SaveInContainer` méthode conserve la clé car il est exécuté en premier, tandis que le code de la `GetKeyFromContainer` méthode charge la clé car il est exécuté en second.

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

La sortie se présente comme suit :

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

## <a name="see-also"></a>Voir aussi

- [Génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md)
- [Chiffrement des données](encrypting-data.md)
- [Déchiffrement des données](decrypting-data.md)
- [Services de chiffrement](cryptographic-services.md)
