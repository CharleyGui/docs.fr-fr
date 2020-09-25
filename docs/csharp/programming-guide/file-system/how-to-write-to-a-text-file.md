---
title: Comment écrire dans un fichier texte-Guide de programmation C#
description: Découvrez comment écrire un fichier texte avec C#. Consultez plusieurs exemples de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 48739852cd1730d71c3b20ae6a9394b57785faa6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170400"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="a7924-104">Comment écrire dans un fichier texte (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a7924-104">How to write to a text file (C# Programming Guide)</span></span>

<span data-ttu-id="a7924-105">Ces exemples montrent différentes manières d'écrire du texte dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a7924-105">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="a7924-106">Les deux premiers exemples utilisent des méthodes pratiques statiques au niveau de la classe <xref:System.IO.File?displayProperty=nameWithType> pour écrire chaque élément de tout `IEnumerable<string>` et une chaîne dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="a7924-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="a7924-107">L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="a7924-107">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="a7924-108">Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="a7924-108">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="a7924-109">Ces exemples écrivent tous des littéraux de chaîne dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="a7924-109">These examples all write string literals to files.</span></span> <span data-ttu-id="a7924-110">Pour mettre en forme le texte écrit dans un fichier, utilisez la méthode <xref:System.String.Format%2A> ou la fonctionnalité d’[interpolation de chaîne](../../language-reference/tokens/interpolated.md) C#.</span><span class="sxs-lookup"><span data-stu-id="a7924-110">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7924-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7924-111">Example</span></span>  

 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a7924-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="a7924-112">Robust Programming</span></span>  

 <span data-ttu-id="a7924-113">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="a7924-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a7924-114">Le fichier existe déjà et est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="a7924-114">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="a7924-115">Le nom du chemin d'accès peut s'avérer trop long.</span><span class="sxs-lookup"><span data-stu-id="a7924-115">The path name may be too long.</span></span>  
  
- <span data-ttu-id="a7924-116">Le disque est peut-être plein.</span><span class="sxs-lookup"><span data-stu-id="a7924-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7924-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7924-117">See also</span></span>

- [<span data-ttu-id="a7924-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a7924-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a7924-119">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a7924-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="a7924-120">Exemple : Enregistrer une collection sur un emplacement de stockage d’application</span><span class="sxs-lookup"><span data-stu-id="a7924-120">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
