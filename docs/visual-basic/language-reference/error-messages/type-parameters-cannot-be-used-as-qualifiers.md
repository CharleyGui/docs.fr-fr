---
title: Les paramètres de type ne peuvent pas être utilisés comme qualificateurs
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 14e6094b0cc129eba86db1808c0f0575955f5e75
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161190"
---
# <a name="bc32098-type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="f2225-102">BC32098 : les paramètres de type ne peuvent pas être utilisés comme qualificateurs</span><span class="sxs-lookup"><span data-stu-id="f2225-102">BC32098: Type parameters cannot be used as qualifiers</span></span>

<span data-ttu-id="f2225-103">Un élément de programmation est qualifié avec une chaîne de qualification qui comprend un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="f2225-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>

<span data-ttu-id="f2225-104">Un paramètre de type représente une spécification pour un type qui doit être fourni lorsque le type générique est construit.</span><span class="sxs-lookup"><span data-stu-id="f2225-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="f2225-105">Il ne représente pas un type défini spécifique.</span><span class="sxs-lookup"><span data-stu-id="f2225-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="f2225-106">Une chaîne de qualification doit inclure uniquement les éléments définis au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f2225-106">A qualification string must include only elements that are defined at compile time.</span></span>

<span data-ttu-id="f2225-107">Le code suivant peut générer cette erreur :</span><span class="sxs-lookup"><span data-stu-id="f2225-107">The following code can generate this error:</span></span>

```vb
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean

    Dim saveText As c.Text
    ' Insert code to look for badText within saveText.
End Function
```

 <span data-ttu-id="f2225-108">**ID d’erreur :** BC32098</span><span class="sxs-lookup"><span data-stu-id="f2225-108">**Error ID:** BC32098</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f2225-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f2225-109">To correct this error</span></span>

1. <span data-ttu-id="f2225-110">Supprimez le paramètre de type de la chaîne de qualification ou remplacez-le par un type défini.</span><span class="sxs-lookup"><span data-stu-id="f2225-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>

2. <span data-ttu-id="f2225-111">Si vous devez utiliser un type construit pour localiser l’élément de programmation qualifié, vous devez utiliser une logique de programme supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="f2225-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2225-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2225-112">See also</span></span>

- [<span data-ttu-id="f2225-113">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="f2225-113">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="f2225-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2225-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="f2225-115">Type List</span><span class="sxs-lookup"><span data-stu-id="f2225-115">Type List</span></span>](../statements/type-list.md)
