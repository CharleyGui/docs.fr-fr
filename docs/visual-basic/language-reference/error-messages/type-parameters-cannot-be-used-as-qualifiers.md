---
title: Les paramètres de type ne peuvent pas être utilisés comme qualificateurs
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592133"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="020a6-102">Les paramètres de type ne peuvent pas être utilisés comme qualificateurs</span><span class="sxs-lookup"><span data-stu-id="020a6-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="020a6-103">Un élément de programmation est qualifié avec une chaîne de qualification qui comprend un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="020a6-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="020a6-104">Un paramètre de type représente une spécification pour un type qui doit être fourni lorsque le type générique est construit.</span><span class="sxs-lookup"><span data-stu-id="020a6-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="020a6-105">Il ne représente pas un type défini spécifique.</span><span class="sxs-lookup"><span data-stu-id="020a6-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="020a6-106">Une chaîne de qualification doit inclure uniquement les éléments définis au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="020a6-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="020a6-107">Les instructions suivantes peuvent générer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="020a6-107">The following statements can generate this error.</span></span>  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="020a6-108">**ID d’erreur :** BC32098</span><span class="sxs-lookup"><span data-stu-id="020a6-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="020a6-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="020a6-109">To correct this error</span></span>  
  
1. <span data-ttu-id="020a6-110">Supprimez le paramètre de type de la chaîne de qualification ou remplacez-le par un type défini.</span><span class="sxs-lookup"><span data-stu-id="020a6-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2. <span data-ttu-id="020a6-111">Si vous devez utiliser un type construit pour localiser l’élément de programmation qualifié, vous devez utiliser une logique de programme supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="020a6-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020a6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="020a6-112">See also</span></span>

- [<span data-ttu-id="020a6-113">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="020a6-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="020a6-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="020a6-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="020a6-115">Liste de types</span><span class="sxs-lookup"><span data-stu-id="020a6-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
