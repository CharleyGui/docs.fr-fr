---
title: Chiffrement de données
description: Découvrez comment chiffrer des données dans .NET, à l’aide d’un algorithme symétrique ou d’un algorithme asymétrique.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 8a8b5988a13ab571284b08c7aaece3542467aa71
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556967"
---
# <a name="encrypting-data"></a>Chiffrement de données

Le chiffrement symétrique et le chiffrement asymétrique utilisent des processus différents. Le chiffrement symétrique est effectué sur des flux. Il est donc utile pour le chiffrement de grandes quantités de données. Le chiffrement asymétrique s'effectue sur un petit nombre d'octets. Il n'est donc utile que pour les petites quantités de données.  
  
## <a name="symmetric-encryption"></a>Chiffrement symétrique  

Les classes managées de chiffrement symétrique sont utilisées avec une classe de flux spéciale appelée <xref:System.Security.Cryptography.CryptoStream> , qui chiffre les données lues dans le flux. La classe **CryptoStream** est initialisée avec une classe de flux managée, une classe qui implémente l' <xref:System.Security.Cryptography.ICryptoTransform> interface (créée à partir d’une classe qui implémente un algorithme de chiffrement) et une <xref:System.Security.Cryptography.CryptoStreamMode> énumération qui décrit le type d’accès autorisé à la classe **CryptoStream**. La classe **CryptoStream** peut être initialisée à l’aide de n’importe quelle classe qui dérive de la <xref:System.IO.Stream> classe, y compris <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> et <xref:System.Net.Sockets.NetworkStream> . À l'aide de ces classes, vous pouvez effectuer le chiffrement symétrique sur une variété d'objets de flux.  
  
L’exemple suivant illustre la création d’une nouvelle instance de la classe d’implémentation par défaut pour l' <xref:System.Security.Cryptography.Aes> algorithme. L’instance est utilisée pour effectuer le chiffrement sur une classe **CryptoStream** . Dans cet exemple, la classe **CryptoStream** est initialisée avec un objet de flux nommé `myStream` qui peut correspondre à n'importe quel type de flux managé. La méthode **CreateEncryptor** de la classe **AES** reçoit la clé et le vecteur d’utilisation utilisés pour le chiffrement. Dans ce cas, la clé et le vecteur d'initialisation par défaut générés à partir de `aes` sont utilisés.
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
Une fois ce code exécuté, toutes les données écrites dans l’objet **CryptoStream** sont chiffrées à l’aide de l’algorithme AES.  
  
L'exemple suivant montre l'intégralité des processus de création de flux, de chiffrement de flux, d'écriture au sein de flux et de fermeture de flux. Cet exemple crée un flux de fichier qui est chiffré à l’aide de la classe **CryptoStream** et de la classe **AES** . Un message est écrit dans le flux chiffré avec la classe <xref:System.IO.StreamWriter> .
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

Le code chiffre le flux à l’aide de l’algorithme symétrique AES et écrit « Hello World ! » dans le flux. Si le code réussit, il crée un fichier chiffré nommé *TestData.txt* et affiche le texte suivant dans la console :  
  
```console  
The text was encrypted.  
```  

Vous pouvez déchiffrer le fichier à l’aide de l’exemple de déchiffrement symétrique dans [déchiffrement des données](decrypting-data.md). Cet exemple et cet exemple spécifient la même clé et le même vecteur d’en-dessus.

Toutefois, si une exception est levée, le code affiche le texte suivant dans la console :  
  
```console  
The encryption failed.  
```

## <a name="asymmetric-encryption"></a>Chiffrement asymétrique

Les algorithmes asymétriques sont généralement utilisés pour chiffrer de petites quantités de données telles qu'une clé symétrique et un vecteur d'initialisation. En règle générale, un utilisateur effectuant un chiffrement asymétrique utilise la clé publique générée par une autre partie. La <xref:System.Security.Cryptography.RSA> classe est fournie par .net à cet effet.  
  
L'exemple suivant utilise les informations de clé publique pour chiffrer une clé symétrique et un vecteur d'initialisation. Deux tableaux d'octets qui représentent la clé publique d'un tiers sont initialisés. Un objet <xref:System.Security.Cryptography.RSAParameters> est initialisé vers ces valeurs. Ensuite, l’objet **RSAParameters** (avec la clé publique qu’il représente) est importé dans une instance **RSA** à l’aide de la <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> méthode. Enfin, la clé privée et le vecteur d’aide créés par une <xref:System.Security.Cryptography.Aes> classe sont chiffrés. Cet exemple nécessite qu'un chiffrement 128 bits soit installé sur les systèmes.  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
    End Sub

End Module
```  
  
```csharp  
using System;
using System.Security.Cryptography;

class Class1
{
    static void Main()
    {
        //Initialize the byte arrays to the public key information.  
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a>Voir aussi

- [Génération de clés pour le chiffrement et le déchiffrement](generating-keys-for-encryption-and-decryption.md)
- [Déchiffrement de données](decrypting-data.md)
- [services de chiffrement](cryptographic-services.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- [Vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC à l’aide du remplissage](vulnerabilities-cbc-mode.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
