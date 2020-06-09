---
title: 'Comment : utiliser la protection des données'
description: Découvrez comment utiliser la protection des données en accédant à l’API de protection des données (DPAPI) dans .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598591"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="3292a-103">Comment : utiliser la protection des données</span><span class="sxs-lookup"><span data-stu-id="3292a-103">How to: Use Data Protection</span></span>
<span data-ttu-id="3292a-104">.NET Framework fournit l'accès à l'API de protection des données (DPAPI), qui permet de chiffrer des données à l'aide des informations de compte de l'utilisateur ou de l'ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="3292a-104">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="3292a-105">Quand vous utilisez l'API de protection des données, vous simplifiez le processus de génération et de stockage explicites de la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="3292a-105">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="3292a-106">Utilisez la classe <xref:System.Security.Cryptography.ProtectedMemory> pour chiffrer un tableau d'octets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3292a-106">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="3292a-107">Cette fonctionnalité est disponible dans Microsoft Windows XP et les systèmes d’exploitation ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="3292a-107">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="3292a-108">Vous pouvez spécifier que la mémoire chiffrée par le processus actuel peut être déchiffrée par le processus actuel uniquement, par tous les processus ou dans le même contexte utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3292a-108">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="3292a-109">Reportez-vous à l'énumération <xref:System.Security.Cryptography.MemoryProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedMemory>.</span><span class="sxs-lookup"><span data-stu-id="3292a-109">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="3292a-110">Utilisez la classe <xref:System.Security.Cryptography.ProtectedData> pour chiffrer une copie d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="3292a-110">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="3292a-111">Cette fonctionnalité est disponible dans Microsoft Windows 2000 et les systèmes d'exploitation ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="3292a-111">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="3292a-112">Vous pouvez spécifier que les données chiffrées par le compte d'utilisateur actuel peuvent être déchiffrées uniquement par le même compte d'utilisateur, ou bien par n'importe quel compte de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3292a-112">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="3292a-113">Reportez-vous à l'énumération <xref:System.Security.Cryptography.DataProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedData>.</span><span class="sxs-lookup"><span data-stu-id="3292a-113">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="3292a-114">Pour chiffrer les données en mémoire à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="3292a-114">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="3292a-115">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection de mémoire.</span><span class="sxs-lookup"><span data-stu-id="3292a-115">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="3292a-116">Pour déchiffrer les données en mémoire à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="3292a-116">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="3292a-117">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection de mémoire.</span><span class="sxs-lookup"><span data-stu-id="3292a-117">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="3292a-118">Pour chiffrer les données d'un fichier ou d'un flux à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="3292a-118">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="3292a-119">Créez une entropie aléatoire.</span><span class="sxs-lookup"><span data-stu-id="3292a-119">Create random entropy.</span></span>  
  
2. <span data-ttu-id="3292a-120">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection des données.</span><span class="sxs-lookup"><span data-stu-id="3292a-120">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="3292a-121">Écrivez les données chiffrées dans un fichier ou un flux.</span><span class="sxs-lookup"><span data-stu-id="3292a-121">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="3292a-122">Pour déchiffrer les données à partir d'un fichier ou d'un flux à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="3292a-122">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="3292a-123">Lisez les données chiffrées à partir d'un fichier ou d'un flux.</span><span class="sxs-lookup"><span data-stu-id="3292a-123">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="3292a-124">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection des données.</span><span class="sxs-lookup"><span data-stu-id="3292a-124">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3292a-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="3292a-125">Example</span></span>  
 <span data-ttu-id="3292a-126">L'exemple de code suivant montre deux formes de chiffrement et de déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="3292a-126">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="3292a-127">Tout d'abord, l'exemple de code chiffre et déchiffre un tableau d'octets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3292a-127">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="3292a-128">Ensuite, l'exemple de code chiffre une copie d'un tableau d'octets, l'enregistre dans un fichier, charge les données à partir du fichier, puis déchiffre les données.</span><span class="sxs-lookup"><span data-stu-id="3292a-128">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="3292a-129">L'exemple affiche les données d'origine, les données chiffrées et les données déchiffrées.</span><span class="sxs-lookup"><span data-stu-id="3292a-129">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3292a-130">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3292a-130">Compiling the Code</span></span>  
  
- <span data-ttu-id="3292a-131">Incluez une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="3292a-131">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="3292a-132">Incluez les espaces de noms <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography> et <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="3292a-132">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3292a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3292a-133">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
