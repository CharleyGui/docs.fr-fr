---
title: Le codage ne peut pas avoir la valeur Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 41565d1aa3b69f6ad92d4bbf2b2f2170014aef87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394477"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="a0d06-102">Le codage ne peut pas avoir la valeur Nothing</span><span class="sxs-lookup"><span data-stu-id="a0d06-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="a0d06-103">Une tentative de lecture ou d’écriture dans un fichier a échoué, car le paramètre `encoding` a la valeur `Nothing` , mais requiert une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="a0d06-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="a0d06-104"><xref:System.Text.Encoding> est utilisé pour déterminer le codage à utiliser lors de l’écriture dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a0d06-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="a0d06-105">La valeur par défaut est UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a0d06-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0d06-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a0d06-106">To correct this error</span></span>  
  
- <span data-ttu-id="a0d06-107">Fournissez une valeur valide pour le paramètre `encoding` .</span><span class="sxs-lookup"><span data-stu-id="a0d06-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d06-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0d06-108">See also</span></span>

- [<span data-ttu-id="a0d06-109">Encodages de fichiers</span><span class="sxs-lookup"><span data-stu-id="a0d06-109">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="a0d06-110">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="a0d06-110">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="a0d06-111">Écriture dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="a0d06-111">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="a0d06-112">My. Computer. FileSystem. ReadAllText</span><span class="sxs-lookup"><span data-stu-id="a0d06-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="a0d06-113">My. Computer. FileSystem. WriteAllText</span><span class="sxs-lookup"><span data-stu-id="a0d06-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
