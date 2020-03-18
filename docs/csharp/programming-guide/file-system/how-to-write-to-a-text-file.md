---
title: Comment écrire sur un fichier texte - Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712245"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="5ef24-102">Comment écrire à un fichier texte (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="5ef24-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="5ef24-103">Ces exemples montrent différentes manières d'écrire du texte dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="5ef24-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="5ef24-104">Les deux premiers exemples utilisent des méthodes pratiques statiques au niveau de la classe <xref:System.IO.File?displayProperty=nameWithType> pour écrire chaque élément de tout `IEnumerable<string>` et une chaîne dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="5ef24-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="5ef24-105">L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="5ef24-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="5ef24-106">Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="5ef24-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="5ef24-107">Ces exemples écrivent tous des littéraux de chaîne dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="5ef24-107">These examples all write string literals to files.</span></span> <span data-ttu-id="5ef24-108">Pour mettre en forme le texte écrit dans un fichier, utilisez la méthode <xref:System.String.Format%2A> ou la fonctionnalité d’[interpolation de chaîne](../../language-reference/tokens/interpolated.md) C#.</span><span class="sxs-lookup"><span data-stu-id="5ef24-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ef24-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5ef24-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5ef24-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="5ef24-110">Robust Programming</span></span>  
 <span data-ttu-id="5ef24-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="5ef24-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5ef24-112">Le fichier existe déjà et est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="5ef24-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="5ef24-113">Le nom du chemin d'accès peut s'avérer trop long.</span><span class="sxs-lookup"><span data-stu-id="5ef24-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="5ef24-114">Le disque est peut-être plein.</span><span class="sxs-lookup"><span data-stu-id="5ef24-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef24-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ef24-115">See also</span></span>

- [<span data-ttu-id="5ef24-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5ef24-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5ef24-117">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5ef24-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="5ef24-118">Exemple : Enregistrer une collection sur un emplacement de stockage d’application</span><span class="sxs-lookup"><span data-stu-id="5ef24-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
