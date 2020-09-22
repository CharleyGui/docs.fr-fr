---
title: Mode de fichier incorrect
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 99b84902ddf032f2ecb6e26400e200bea862dfdf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875144"
---
# <a name="bad-file-mode"></a><span data-ttu-id="da88c-102">Mode de fichier incorrect</span><span class="sxs-lookup"><span data-stu-id="da88c-102">Bad file mode</span></span>

<span data-ttu-id="da88c-103">Les instructions utilisées pour manipuler le contenu d’un fichier doivent être appropriées au mode dans lequel le fichier a été ouvert.</span><span class="sxs-lookup"><span data-stu-id="da88c-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="da88c-104">Les causes possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="da88c-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="da88c-105">Une `FilePutObject` `FileGetObject` instruction ou spécifie un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="da88c-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="da88c-106">Une `Print` instruction spécifie un fichier ouvert pour un mode d’accès autre que `Output` ou `Append` .</span><span class="sxs-lookup"><span data-stu-id="da88c-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="da88c-107">Une `Input` instruction spécifie un fichier ouvert pour un mode d’accès autre que `Input`</span><span class="sxs-lookup"><span data-stu-id="da88c-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="da88c-108">Tentative d’écriture dans un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="da88c-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da88c-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="da88c-109">To correct this error</span></span>  
  
- <span data-ttu-id="da88c-110">Assurez-vous `FilePutObject` `FileGetObject` que et ne font référence qu’à des fichiers ouverts pour `Random` ou `Binary` accessibles.</span><span class="sxs-lookup"><span data-stu-id="da88c-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="da88c-111">Assurez-vous que `Print` spécifie un fichier ouvert pour le `Output` `Append` mode d’accès ou.</span><span class="sxs-lookup"><span data-stu-id="da88c-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="da88c-112">Si ce n’est pas le cas, utilisez une autre instruction pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.</span><span class="sxs-lookup"><span data-stu-id="da88c-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="da88c-113">Assurez-vous que `Input` spécifie un fichier ouvert pour `Input` .</span><span class="sxs-lookup"><span data-stu-id="da88c-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="da88c-114">Si ce n’est pas le cas, utilisez une autre instruction pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.</span><span class="sxs-lookup"><span data-stu-id="da88c-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="da88c-115">Si vous écrivez dans un fichier en lecture seule, modifiez l’état de lecture/écriture du fichier ou n’essayez pas d’écrire dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="da88c-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="da88c-116">Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="da88c-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da88c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da88c-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="da88c-118">Résolution des problèmes : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="da88c-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
