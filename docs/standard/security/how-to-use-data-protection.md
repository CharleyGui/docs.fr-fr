---
title: 'Comment : utiliser la protection des données'
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
ms.openlocfilehash: 0efd677f11189b28b8efc184c04b30a047ab942b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706030"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="cbb66-102">Comment : utiliser la protection des données</span><span class="sxs-lookup"><span data-stu-id="cbb66-102">How to: Use Data Protection</span></span>
<span data-ttu-id="cbb66-103">.NET Framework fournit l'accès à l'API de protection des données (DPAPI), qui permet de chiffrer des données à l'aide des informations de compte de l'utilisateur ou de l'ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="cbb66-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="cbb66-104">Quand vous utilisez l'API de protection des données, vous simplifiez le processus de génération et de stockage explicites de la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="cbb66-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="cbb66-105">Utilisez la classe <xref:System.Security.Cryptography.ProtectedMemory> pour chiffrer un tableau d'octets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="cbb66-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="cbb66-106">Cette fonctionnalité est disponible dans Microsoft Windows XP et les systèmes d’exploitation ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="cbb66-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="cbb66-107">Vous pouvez spécifier que la mémoire chiffrée par le processus actuel peut être déchiffrée par le processus actuel uniquement, par tous les processus ou dans le même contexte utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cbb66-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="cbb66-108">Reportez-vous à l'énumération <xref:System.Security.Cryptography.MemoryProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedMemory>.</span><span class="sxs-lookup"><span data-stu-id="cbb66-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="cbb66-109">Utilisez la classe <xref:System.Security.Cryptography.ProtectedData> pour chiffrer une copie d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="cbb66-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="cbb66-110">Cette fonctionnalité est disponible dans Microsoft Windows 2000 et les systèmes d'exploitation ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="cbb66-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="cbb66-111">Vous pouvez spécifier que les données chiffrées par le compte d'utilisateur actuel peuvent être déchiffrées uniquement par le même compte d'utilisateur, ou bien par n'importe quel compte de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cbb66-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="cbb66-112">Reportez-vous à l'énumération <xref:System.Security.Cryptography.DataProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedData>.</span><span class="sxs-lookup"><span data-stu-id="cbb66-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="cbb66-113">Pour chiffrer les données en mémoire à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="cbb66-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="cbb66-114">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection de mémoire.</span><span class="sxs-lookup"><span data-stu-id="cbb66-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="cbb66-115">Pour déchiffrer les données en mémoire à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="cbb66-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="cbb66-116">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection de mémoire.</span><span class="sxs-lookup"><span data-stu-id="cbb66-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="cbb66-117">Pour chiffrer les données d'un fichier ou d'un flux à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="cbb66-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="cbb66-118">Créez une entropie aléatoire.</span><span class="sxs-lookup"><span data-stu-id="cbb66-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="cbb66-119">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection des données.</span><span class="sxs-lookup"><span data-stu-id="cbb66-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="cbb66-120">Écrivez les données chiffrées dans un fichier ou un flux.</span><span class="sxs-lookup"><span data-stu-id="cbb66-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="cbb66-121">Pour déchiffrer les données à partir d'un fichier ou d'un flux à l'aide de la protection des données</span><span class="sxs-lookup"><span data-stu-id="cbb66-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="cbb66-122">Lisez les données chiffrées à partir d'un fichier ou d'un flux.</span><span class="sxs-lookup"><span data-stu-id="cbb66-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="cbb66-123">Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection des données.</span><span class="sxs-lookup"><span data-stu-id="cbb66-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbb66-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbb66-124">Example</span></span>  
 <span data-ttu-id="cbb66-125">L'exemple de code suivant montre deux formes de chiffrement et de déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="cbb66-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="cbb66-126">Tout d'abord, l'exemple de code chiffre et déchiffre un tableau d'octets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="cbb66-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="cbb66-127">Ensuite, l'exemple de code chiffre une copie d'un tableau d'octets, l'enregistre dans un fichier, charge les données à partir du fichier, puis déchiffre les données.</span><span class="sxs-lookup"><span data-stu-id="cbb66-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="cbb66-128">L'exemple affiche les données d'origine, les données chiffrées et les données déchiffrées.</span><span class="sxs-lookup"><span data-stu-id="cbb66-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cbb66-129">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="cbb66-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="cbb66-130">Incluez une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="cbb66-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="cbb66-131">Incluez les espaces de noms <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography> et <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="cbb66-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb66-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbb66-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
