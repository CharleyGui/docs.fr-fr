---
description: '##pragma checksum - Référence C#'
title: '##pragma checksum - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: df665704ac813adbbf6473e81fad0a1c7ff616d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168567"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="67eb0-103">#pragma checksum (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="67eb0-103">#pragma checksum (C# Reference)</span></span>

<span data-ttu-id="67eb0-104">Génère des sommes de contrôle pour les fichiers sources afin de faciliter le débogage des pages ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="67eb0-104">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67eb0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67eb0-105">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="67eb0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67eb0-106">Parameters</span></span>  

 `"filename"`  
 <span data-ttu-id="67eb0-107">Nom du fichier dont les modifications ou les mises à jour doivent faire l’objet d’une surveillance.</span><span class="sxs-lookup"><span data-stu-id="67eb0-107">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="67eb0-108">Identificateur global unique (GUID) du fichier pour l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="67eb0-108">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="67eb0-109">Chaîne de chiffres hexadécimaux représentant les octets de la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="67eb0-109">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="67eb0-110">Doit être un nombre pair de chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="67eb0-110">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="67eb0-111">S’il y a un nombre impair de chiffres, un avertissement est généré au moment de la compilation et la directive est ignorée.</span><span class="sxs-lookup"><span data-stu-id="67eb0-111">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67eb0-112">Notes</span><span class="sxs-lookup"><span data-stu-id="67eb0-112">Remarks</span></span>  

 <span data-ttu-id="67eb0-113">Le débogueur Visual Studio utilise une somme de contrôle pour s’assurer de toujours trouver la bonne source.</span><span class="sxs-lookup"><span data-stu-id="67eb0-113">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="67eb0-114">Le compilateur calcule la somme de contrôle pour un fichier source, puis envoie la sortie vers le fichier de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="67eb0-114">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="67eb0-115">Le débogueur utilise ensuite le fichier PDB à comparer avec la somme de contrôle qu’il calcule pour le fichier source.</span><span class="sxs-lookup"><span data-stu-id="67eb0-115">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="67eb0-116">Cette solution ne fonctionne pas pour les projets ASP.NET, car la somme de contrôle est calculée pour le fichier source généré, au lieu du fichier .aspx.</span><span class="sxs-lookup"><span data-stu-id="67eb0-116">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="67eb0-117">Pour résoudre ce problème, `#pragma checksum` fournit une prise en charge de la somme de contrôle pour les pages ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="67eb0-117">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="67eb0-118">Quand vous créez un projet ASP.NET dans Visual C#, le fichier source généré contient une somme de contrôle pour le fichier .aspx, à partir duquel la source est générée.</span><span class="sxs-lookup"><span data-stu-id="67eb0-118">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="67eb0-119">Le compilateur écrit ensuite ces informations dans le fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="67eb0-119">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="67eb0-120">Si le compilateur ne rencontre aucune directive `#pragma checksum` dans le fichier, il calcule la somme de contrôle et écrit la valeur dans le fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="67eb0-120">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67eb0-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="67eb0-121">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="67eb0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67eb0-122">See also</span></span>

- [<span data-ttu-id="67eb0-123">Référence C#</span><span class="sxs-lookup"><span data-stu-id="67eb0-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="67eb0-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="67eb0-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="67eb0-125">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="67eb0-125">C# Preprocessor Directives</span></span>](./index.md)
