---
title: Chiffrement et déchiffrement de chaînes dans Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee8691fedb537d1aa588eaac61624b445da64d1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944425"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="c5bd0-102">Procédure pas à pas : Chiffrement et déchiffrement de chaînes dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5bd0-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="c5bd0-103">Cette procédure pas à pas vous montre comment <xref:System.Security.Cryptography.DESCryptoServiceProvider> utiliser la classe pour chiffrer et déchiffrer des chaînes à l’aide de la version du fournisseur de services<xref:System.Security.Cryptography.TripleDES>de chiffrement (CSP) de l’algorithme Triple Data Encryption Standard ().</span><span class="sxs-lookup"><span data-stu-id="c5bd0-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="c5bd0-104">La première étape consiste à créer une classe wrapper simple qui encapsule l’algorithme 3DES et stocke les données chiffrées sous la forme d’une chaîne codée en base 64.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="c5bd0-105">Ce wrapper est ensuite utilisé pour stocker en toute sécurité les données utilisateur privées dans un fichier texte accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="c5bd0-106">Vous pouvez utiliser le chiffrement pour protéger les secrets des utilisateurs (par exemple, les mots de passe) et rendre les informations d’identification illisibles pour les utilisateurs non autorisés.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="c5bd0-107">Cela peut empêcher le vol de l’identité d’un utilisateur autorisé, ce qui protège les ressources de l’utilisateur et fournit une non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="c5bd0-108">Le chiffrement peut également empêcher les utilisateurs non autorisés d’accéder aux données d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="c5bd0-109">Pour plus d’informations, consultez [Services de cryptographie](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="c5bd0-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c5bd0-110">Les algorithmes Rijndael (désormais appelé Advanced Encryption Standard [AES]) et 3DES (Triple Data Encryption Standard) offrent une plus grande sécurité que DES, car ils nécessitent beaucoup de ressources informatiques.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="c5bd0-111">Pour plus d’informations, consultez <xref:System.Security.Cryptography.DES> et <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="c5bd0-112">Pour créer le wrapper de chiffrement</span><span class="sxs-lookup"><span data-stu-id="c5bd0-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="c5bd0-113">Créez la `Simple3Des` classe pour encapsuler les méthodes de chiffrement et de déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="c5bd0-114">Ajoutez une importation de l’espace de noms Cryptography au début du fichier qui contient la `Simple3Des` classe.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="c5bd0-115">Dans la `Simple3Des` classe, ajoutez un champ privé pour stocker le fournisseur de services de chiffrement 3DES.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="c5bd0-116">Ajoutez une méthode privée qui crée un tableau d’octets d’une longueur spécifiée à partir du hachage de la clé spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="c5bd0-117">Ajoutez un constructeur pour initialiser le fournisseur de services de chiffrement 3DES.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="c5bd0-118">Le `key` paramètre contrôle les `EncryptData` méthodes `DecryptData` et.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="c5bd0-119">Ajoutez une méthode publique qui chiffre une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="c5bd0-120">Ajoutez une méthode publique qui déchiffre une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="c5bd0-121">La classe wrapper peut maintenant être utilisée pour protéger les ressources de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="c5bd0-122">Dans cet exemple, il est utilisé pour stocker en toute sécurité des données utilisateur privées dans un fichier texte accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="c5bd0-123">Pour tester le wrapper de chiffrement</span><span class="sxs-lookup"><span data-stu-id="c5bd0-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="c5bd0-124">Dans une classe distincte, ajoutez une méthode qui utilise la méthode du `EncryptData` wrapper pour chiffrer une chaîne et l’écrire dans le dossier Mes documents de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="c5bd0-125">Ajoutez une méthode qui lit la chaîne chiffrée à partir du dossier Mes documents de l’utilisateur et déchiffre la chaîne avec la `DecryptData` méthode du wrapper.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="c5bd0-126">Ajoutez le code de l’interface utilisateur `TestEncoding` pour `TestDecoding` appeler les méthodes et.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="c5bd0-127">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-127">Run the application.</span></span>  
  
     <span data-ttu-id="c5bd0-128">Lorsque vous testez l’application, Notez qu’elle ne déchiffrera pas les données si vous fournissez un mot de passe incorrect.</span><span class="sxs-lookup"><span data-stu-id="c5bd0-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bd0-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5bd0-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="c5bd0-130">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="c5bd0-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
