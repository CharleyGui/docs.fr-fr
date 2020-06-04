---
title: Erreur d’accès au chemin de fichier
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: dfe96cd6eaa673438849fe8f799d46fa2617bfdd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387255"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="ea7a5-102">Erreur dans le chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="ea7a5-102">Path/File access error</span></span>
<span data-ttu-id="ea7a5-103">Au cours d’une opération d’accès au fichier ou d’accès au disque, le système d’exploitation n’a pas pu établir de connexion entre le chemin d’accès et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ea7a5-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ea7a5-104">To correct this error</span></span>  
  
1. <span data-ttu-id="ea7a5-105">Assurez-vous que la spécification de fichier est correctement mise en forme.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="ea7a5-106">Un nom de fichier peut contenir un chemin d’accès complet (absolu) ou relatif.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="ea7a5-107">Un chemin d’accès complet commence par le nom du lecteur (si le chemin d’accès se trouve sur un autre lecteur) et indique le chemin d’accès explicite de la racine au fichier.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="ea7a5-108">Tout chemin d’accès qui n’est pas complet est relatif au lecteur et au répertoire actifs.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="ea7a5-109">Assurez-vous que vous n’avez pas tenté d’enregistrer un fichier qui remplacerait un fichier en lecture seule existant.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="ea7a5-110">Si c’est le cas, modifiez l’attribut de lecture seule du fichier cible ou enregistrez le fichier sous un autre nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="ea7a5-111">Assurez-vous que vous n’avez pas tenté d’ouvrir un fichier en lecture seule en `Output` mode séquentiel ou en `Append` mode.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="ea7a5-112">Si c’est le cas, ouvrez le fichier en `Input` mode ou modifiez l’attribut de lecture seule du fichier.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="ea7a5-113">Assurez-vous que vous n’avez pas tenté de modifier un projet de Visual Basic dans une base de données ou un document.</span><span class="sxs-lookup"><span data-stu-id="ea7a5-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7a5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea7a5-114">See also</span></span>

- [<span data-ttu-id="ea7a5-115">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="ea7a5-115">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
