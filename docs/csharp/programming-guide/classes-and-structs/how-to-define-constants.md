---
title: 'Comment : définir des constantes en C#'
description: Découvrez comment définir des constantes en C#, qui sont des champs dont les valeurs sont définies au moment de la compilation. Utilisez des constantes pour fournir des noms explicites pour les valeurs spéciales.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: afa2799cf76f976e332f91b631dc90e2799a0aa0
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864642"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="bc076-104">Comment définir des constantes en C\#</span><span class="sxs-lookup"><span data-stu-id="bc076-104">How to define constants in C\#</span></span>
<span data-ttu-id="bc076-105">Les constantes sont des champs dont les valeurs sont définies au moment de la compilation et ne sont pas modifiables.</span><span class="sxs-lookup"><span data-stu-id="bc076-105">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="bc076-106">Utilisez des constantes pour fournir des noms explicites au lieu de littéraux numériques (« nombres magiques ») pour les valeurs spéciales.</span><span class="sxs-lookup"><span data-stu-id="bc076-106">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc076-107">En C#, la directive de préprocesseur [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) ne peut pas être utilisée pour définir des constantes de la manière généralement utilisée en C et C++.</span><span class="sxs-lookup"><span data-stu-id="bc076-107">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="bc076-108">Pour définir des valeurs constantes de types intégraux (`int`, `byte`, etc.), utilisez un type énuméré.</span><span class="sxs-lookup"><span data-stu-id="bc076-108">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="bc076-109">Pour plus d’informations, consultez [enum](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="bc076-109">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="bc076-110">Pour définir des constantes non intégrales, une approche consiste à les regrouper dans une classe statique unique nommée `Constants`.</span><span class="sxs-lookup"><span data-stu-id="bc076-110">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="bc076-111">Cette opération exige que toutes les références aux constantes soient précédées par le nom de classe, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bc076-111">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc076-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc076-112">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="bc076-113">L’utilisation du qualificateur de nom de classe permet de garantir que les personnes qui utilisent la constante, dont vous-même, comprennent qu’il s’agit d’une valeur constante et qu’elle ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="bc076-113">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc076-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc076-114">See also</span></span>

- [<span data-ttu-id="bc076-115">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="bc076-115">Classes and Structs</span></span>](./index.md)
