---
title: Constantes (référence des API non managées)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
ms.openlocfilehash: 19defe9c6c19bc04eb3c9ddaee386ef1ee409de5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673928"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="7e230-102">Constantes (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="7e230-102">Constants (Unmanaged API Reference)</span></span>

<span data-ttu-id="7e230-103">Cette rubrique décrit le type de langage, le fournisseur de langage et les constantes de type de document qui sont définis dans CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="7e230-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="7e230-104">Constantes de type de langage</span><span class="sxs-lookup"><span data-stu-id="7e230-104">Language Type Constants</span></span>  

 <span data-ttu-id="7e230-105">Le tableau suivant montre les constantes de type de langage, qui représentent des GUID qui identifient les langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="7e230-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="7e230-106">Symbole</span><span class="sxs-lookup"><span data-stu-id="7e230-106">Symbol</span></span>|<span data-ttu-id="7e230-107">Description</span><span class="sxs-lookup"><span data-stu-id="7e230-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7e230-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="7e230-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="7e230-109">Indique le langage C.</span><span class="sxs-lookup"><span data-stu-id="7e230-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="7e230-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="7e230-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="7e230-111">Indique le langage C++.</span><span class="sxs-lookup"><span data-stu-id="7e230-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="7e230-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="7e230-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="7e230-113">Indique le langage C#.</span><span class="sxs-lookup"><span data-stu-id="7e230-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="7e230-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="7e230-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="7e230-115">Indique la langue de base.</span><span class="sxs-lookup"><span data-stu-id="7e230-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="7e230-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="7e230-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="7e230-117">Indique le langage Java.</span><span class="sxs-lookup"><span data-stu-id="7e230-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="7e230-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="7e230-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="7e230-119">Indique le langage COBOL.</span><span class="sxs-lookup"><span data-stu-id="7e230-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="7e230-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="7e230-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="7e230-121">Indique le langage Pascal.</span><span class="sxs-lookup"><span data-stu-id="7e230-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="7e230-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="7e230-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="7e230-123">Indique le code assembleur MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="7e230-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="7e230-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="7e230-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="7e230-125">Indique le langage JScript.</span><span class="sxs-lookup"><span data-stu-id="7e230-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="7e230-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="7e230-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="7e230-127">Indique le langage SMC.</span><span class="sxs-lookup"><span data-stu-id="7e230-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="7e230-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="7e230-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="7e230-129">Indique que le langage C++ est activé pour le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e230-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="7e230-130">Constantes de fournisseur de langue</span><span class="sxs-lookup"><span data-stu-id="7e230-130">Language Vendor Constants</span></span>  

 <span data-ttu-id="7e230-131">Le tableau suivant montre les constantes de fournisseur de langages, qui représentent des GUID qui identifient les fournisseurs de langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="7e230-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="7e230-132">Symbole</span><span class="sxs-lookup"><span data-stu-id="7e230-132">Symbol</span></span>|<span data-ttu-id="7e230-133">Description</span><span class="sxs-lookup"><span data-stu-id="7e230-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7e230-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="7e230-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="7e230-135">Indique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7e230-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="7e230-136">Constantes de type de document</span><span class="sxs-lookup"><span data-stu-id="7e230-136">Document Type Constants</span></span>  

 <span data-ttu-id="7e230-137">Le tableau suivant présente les constantes de type de document, qui représentent des GUID qui identifient les types de documents.</span><span class="sxs-lookup"><span data-stu-id="7e230-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="7e230-138">Symbole</span><span class="sxs-lookup"><span data-stu-id="7e230-138">Symbol</span></span>|<span data-ttu-id="7e230-139">Description</span><span class="sxs-lookup"><span data-stu-id="7e230-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7e230-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="7e230-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="7e230-141">Indique un document texte.</span><span class="sxs-lookup"><span data-stu-id="7e230-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="7e230-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="7e230-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="7e230-143">Indique un document non-texte.</span><span class="sxs-lookup"><span data-stu-id="7e230-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e230-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e230-144">See also</span></span>

- [<span data-ttu-id="7e230-145">Informations de référence sur les API non managées</span><span class="sxs-lookup"><span data-stu-id="7e230-145">Unmanaged API Reference</span></span>](index.md)
