---
title: Mode de fichier incorrect
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409867"
---
# <a name="bad-file-mode"></a><span data-ttu-id="ccb24-102">Mode de fichier incorrect</span><span class="sxs-lookup"><span data-stu-id="ccb24-102">Bad file mode</span></span>
<span data-ttu-id="ccb24-103">Les instructions utilisées pour manipuler le contenu d’un fichier doivent être appropriées au mode dans lequel le fichier a été ouvert.</span><span class="sxs-lookup"><span data-stu-id="ccb24-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="ccb24-104">Les causes possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ccb24-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="ccb24-105">Une `FilePutObject` `FileGetObject` instruction ou spécifie un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="ccb24-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="ccb24-106">Une `Print` instruction spécifie un fichier ouvert pour un mode d’accès autre que `Output` ou `Append` .</span><span class="sxs-lookup"><span data-stu-id="ccb24-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="ccb24-107">Une `Input` instruction spécifie un fichier ouvert pour un mode d’accès autre que`Input`</span><span class="sxs-lookup"><span data-stu-id="ccb24-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="ccb24-108">Tentative d’écriture dans un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ccb24-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ccb24-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ccb24-109">To correct this error</span></span>  
  
- <span data-ttu-id="ccb24-110">Assurez-vous `FilePutObject` `FileGetObject` que et ne font référence qu’à des fichiers ouverts pour `Random` ou `Binary` accessibles.</span><span class="sxs-lookup"><span data-stu-id="ccb24-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="ccb24-111">Assurez-vous que `Print` spécifie un fichier ouvert pour le `Output` `Append` mode d’accès ou.</span><span class="sxs-lookup"><span data-stu-id="ccb24-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="ccb24-112">Si ce n’est pas le cas, utilisez une autre instruction pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.</span><span class="sxs-lookup"><span data-stu-id="ccb24-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="ccb24-113">Assurez-vous que `Input` spécifie un fichier ouvert pour `Input` .</span><span class="sxs-lookup"><span data-stu-id="ccb24-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="ccb24-114">Si ce n’est pas le cas, utilisez une autre instruction pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.</span><span class="sxs-lookup"><span data-stu-id="ccb24-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="ccb24-115">Si vous écrivez dans un fichier en lecture seule, modifiez l’état de lecture/écriture du fichier ou n’essayez pas d’écrire dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ccb24-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="ccb24-116">Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="ccb24-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb24-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccb24-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="ccb24-118">Résolution des problèmes : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="ccb24-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
