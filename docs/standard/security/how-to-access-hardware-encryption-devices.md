---
title: 'Procédure : accéder aux appareils de chiffrement matériel'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: 7cd3aab80a8388c1d4ce08e4ae94aae84cfff239
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557136"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="e7241-102">Procédure : accéder aux appareils de chiffrement matériel</span><span class="sxs-lookup"><span data-stu-id="e7241-102">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="e7241-103">Cet article s’applique à Windows.</span><span class="sxs-lookup"><span data-stu-id="e7241-103">This article applies to Windows.</span></span>

<span data-ttu-id="e7241-104">Vous pouvez utiliser la classe <xref:System.Security.Cryptography.CspParameters> pour accéder aux périphériques de chiffrement matériel.</span><span class="sxs-lookup"><span data-stu-id="e7241-104">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="e7241-105">Par exemple, vous pouvez utiliser cette classe pour intégrer votre application à une carte à puce, à un générateur matériel de nombres aléatoires ou à une implémentation matérielle d'un algorithme de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="e7241-105">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="e7241-106">La classe <xref:System.Security.Cryptography.CspParameters> crée un fournisseur de services de chiffrement (CSP) qui accède à un périphérique de chiffrement matériel correctement installé.</span><span class="sxs-lookup"><span data-stu-id="e7241-106">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="e7241-107">Vous pouvez vérifier la disponibilité d'un fournisseur de services de chiffrement en inspectant la clé de Registre suivante à l'aide de l'Éditeur du Registre (Regedit.exe) : HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="e7241-107">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="e7241-108">Pour signer des données à l'aide d'une carte de clé</span><span class="sxs-lookup"><span data-stu-id="e7241-108">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="e7241-109">Créez une instance de la classe <xref:System.Security.Cryptography.CspParameters>, en passant le type de fournisseur entier et le nom du fournisseur au constructeur.</span><span class="sxs-lookup"><span data-stu-id="e7241-109">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="e7241-110">Passez les indicateurs appropriés à la propriété <xref:System.Security.Cryptography.CspParameters.Flags%2A> du nouvel objet <xref:System.Security.Cryptography.CspParameters>.</span><span class="sxs-lookup"><span data-stu-id="e7241-110">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="e7241-111">Par exemple, passez l'indicateur <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.</span><span class="sxs-lookup"><span data-stu-id="e7241-111">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="e7241-112">Créez une instance d'une classe <xref:System.Security.Cryptography.AsymmetricAlgorithm> (par exemple, la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>), en passant l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur.</span><span class="sxs-lookup"><span data-stu-id="e7241-112">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="e7241-113">Signez vos données à l'aide de l'une des méthodes `Sign`, puis vérifiez vos données à l'aide de l'une des méthodes `Verify`.</span><span class="sxs-lookup"><span data-stu-id="e7241-113">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="e7241-114">Pour générer un nombre aléatoire à l'aide d'un générateur matériel de nombres aléatoires</span><span class="sxs-lookup"><span data-stu-id="e7241-114">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="e7241-115">Créez une instance de la classe <xref:System.Security.Cryptography.CspParameters>, en passant le type de fournisseur entier et le nom du fournisseur au constructeur.</span><span class="sxs-lookup"><span data-stu-id="e7241-115">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="e7241-116">Créez une instance de <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, en passant l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur.</span><span class="sxs-lookup"><span data-stu-id="e7241-116">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="e7241-117">Créez une valeur aléatoire à l'aide de la méthode <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> ou <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7241-117">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7241-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7241-118">Example</span></span>

<span data-ttu-id="e7241-119">L'exemple de code suivant montre comment signer des données à l'aide d'une carte à puce.</span><span class="sxs-lookup"><span data-stu-id="e7241-119">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="e7241-120">L'exemple de code crée un objet <xref:System.Security.Cryptography.CspParameters> qui expose une carte à puce, puis initialise un objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> à l'aide du fournisseur de services de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="e7241-120">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="e7241-121">L'exemple de code signe et vérifie certaines données.</span><span class="sxs-lookup"><span data-stu-id="e7241-121">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="e7241-122">En raison de problèmes de collision avec SHA1, nous vous recommandons SHA256 ou une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="e7241-122">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7241-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e7241-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="e7241-124">Incluez les espaces de noms <xref:System> et <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="e7241-124">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="e7241-125">Vous devez disposer d'un lecteur de carte à puce et de pilotes installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e7241-125">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="e7241-126">Vous devez initialiser l'objet <xref:System.Security.Cryptography.CspParameters> à l'aide des informations spécifiques à votre lecteur de cartes.</span><span class="sxs-lookup"><span data-stu-id="e7241-126">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="e7241-127">Pour plus d'informations, consultez la documentation de votre lecteur de cartes.</span><span class="sxs-lookup"><span data-stu-id="e7241-127">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7241-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7241-128">See also</span></span>

- [<span data-ttu-id="e7241-129">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="e7241-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="e7241-130">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="e7241-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="e7241-131">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="e7241-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="e7241-132">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e7241-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
