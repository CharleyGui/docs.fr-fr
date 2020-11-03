---
title: 'Procédure : utiliser la protection des données'
description: Découvrez comment utiliser la protection des données en accédant à l’API de protection des données (DPAPI) dans .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: d3fe7ef3ddbc6e75a248101829b11a8abcb3c15a
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282051"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="8d77c-103">Procédure : utiliser la protection des données</span><span class="sxs-lookup"><span data-stu-id="8d77c-103">How to: Use Data Protection</span></span>

> [!NOTE]
> <span data-ttu-id="8d77c-104">Cet article s’applique à Windows.</span><span class="sxs-lookup"><span data-stu-id="8d77c-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="8d77c-105">Pour plus d’informations sur la ASP.NET Core, consultez [protection des données ASP.net Core](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="8d77c-105">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="8d77c-106">.NET fournit un accès à l’API de protection des données (DPAPI), qui vous permet de chiffrer les données à l’aide des informations du compte d’utilisateur ou de l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="8d77c-106">.NET provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="8d77c-107">Quand vous utilisez l'API de protection des données, vous simplifiez le processus de génération et de stockage explicites de la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="8d77c-107">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
<span data-ttu-id="8d77c-108">Utilisez la classe <xref:System.Security.Cryptography.ProtectedData> pour chiffrer une copie d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="8d77c-108">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="8d77c-109">Cette fonctionnalité est disponible dans .NET Framework, .NET Core et .NET 5.</span><span class="sxs-lookup"><span data-stu-id="8d77c-109">This functionality is available in .NET Framework, .NET Core, and .NET 5.</span></span>  <span data-ttu-id="8d77c-110">Vous pouvez spécifier que les données chiffrées par le compte d'utilisateur actuel peuvent être déchiffrées uniquement par le même compte d'utilisateur, ou bien par n'importe quel compte de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8d77c-110">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="8d77c-111">Reportez-vous à l'énumération <xref:System.Security.Cryptography.DataProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedData>.</span><span class="sxs-lookup"><span data-stu-id="8d77c-111">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
## <a name="encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="8d77c-112">Chiffrer des données dans un fichier ou un flux à l’aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="8d77c-112">Encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="8d77c-113">Créez une entropie aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8d77c-113">Create random entropy.</span></span>  
  
2. <span data-ttu-id="8d77c-114">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection des données.</span><span class="sxs-lookup"><span data-stu-id="8d77c-114">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="8d77c-115">Écrivez les données chiffrées dans un fichier ou un flux.</span><span class="sxs-lookup"><span data-stu-id="8d77c-115">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="8d77c-116">Pour déchiffrer les données à partir d'un fichier ou d'un flux à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="8d77c-116">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="8d77c-117">Lisez les données chiffrées à partir d'un fichier ou d'un flux.</span><span class="sxs-lookup"><span data-stu-id="8d77c-117">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="8d77c-118">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection des données.</span><span class="sxs-lookup"><span data-stu-id="8d77c-118">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d77c-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d77c-119">Example</span></span>

<span data-ttu-id="8d77c-120">L'exemple de code suivant montre deux formes de chiffrement et de déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="8d77c-120">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="8d77c-121">Tout d'abord, l'exemple de code chiffre et déchiffre un tableau d'octets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="8d77c-121">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="8d77c-122">Ensuite, l'exemple de code chiffre une copie d'un tableau d'octets, l'enregistre dans un fichier, charge les données à partir du fichier, puis déchiffre les données.</span><span class="sxs-lookup"><span data-stu-id="8d77c-122">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="8d77c-123">L'exemple affiche les données d'origine, les données chiffrées et les données déchiffrées.</span><span class="sxs-lookup"><span data-stu-id="8d77c-123">The example displays the original data, the encrypted data, and the decrypted data.</span></span>

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d77c-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8d77c-124">Compiling the Code</span></span>  

<span data-ttu-id="8d77c-125">Cet exemple compile et s’exécute uniquement lorsque vous ciblez .NET Framework et que vous exécutez sur Windows.</span><span class="sxs-lookup"><span data-stu-id="8d77c-125">This example compiles and runs only when targeting .NET Framework and running on Windows.</span></span>

- <span data-ttu-id="8d77c-126">Incluez une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="8d77c-126">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="8d77c-127">Incluez les espaces de noms <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography> et <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="8d77c-127">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d77c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d77c-128">See also</span></span>

- [<span data-ttu-id="8d77c-129">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="8d77c-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="8d77c-130">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="8d77c-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="8d77c-131">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="8d77c-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [<span data-ttu-id="8d77c-132">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d77c-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
