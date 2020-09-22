---
title: Longueur d'enregistrement incorrecte
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869258"
---
# <a name="bad-record-length"></a><span data-ttu-id="c2977-102">Longueur d'enregistrement incorrecte</span><span class="sxs-lookup"><span data-stu-id="c2977-102">Bad record length</span></span>

<span data-ttu-id="c2977-103">Cette erreur peut avoir plusieurs causes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2977-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="c2977-104">La longueur d’une variable d’enregistrement spécifiée dans `FileGet` une `FileGetObject` `FilePut` instruction, ou `FilePutObject` diffère de la longueur spécifiée dans l' `FileOpen` instruction correspondante.</span><span class="sxs-lookup"><span data-stu-id="c2977-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
- <span data-ttu-id="c2977-105">La variable dans une `FilePut` `FilePutObject` instruction ou est ou contient une chaîne de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="c2977-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
- <span data-ttu-id="c2977-106">La variable dans `FilePut` ou `FilePutObject` est ou comprend un `Variant` type.</span><span class="sxs-lookup"><span data-stu-id="c2977-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c2977-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c2977-107">To correct this error</span></span>  
  
1. <span data-ttu-id="c2977-108">Assurez-vous que la somme des tailles des variables de longueur fixe dans le type défini par l’utilisateur qui définit le type de la variable d’enregistrement est identique à la valeur indiquée dans la `FileOpen` clause de l’instruction `Len` .</span><span class="sxs-lookup"><span data-stu-id="c2977-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="c2977-109">Si la variable dans une `FilePut` `FilePutObject` instruction ou est ou contient une chaîne de longueur variable, assurez-vous que la chaîne de longueur variable comporte au moins 2 caractères plus courts que la longueur d’enregistrement spécifiée dans la `Len` clause de l' `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="c2977-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="c2977-110">Si la variable dans un `FilePut` ou `FilePutObject` est ou s’il comprend une, assurez-vous que `Variant` la chaîne de longueur variable est d’au moins 4 octets plus courts que la longueur d’enregistrement spécifiée dans la `Len` clause de l' `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="c2977-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2977-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2977-111">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
