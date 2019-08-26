---
title: 'Procédure : Définir des constantes en C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: ba5bc3d03dcaf5c8be94936a453a439670e8dc1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924486"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="8a998-102">Procédure : Définir des constantes en C\#</span><span class="sxs-lookup"><span data-stu-id="8a998-102">How to: Define Constants in C\#</span></span>
<span data-ttu-id="8a998-103">Les constantes sont des champs dont les valeurs sont définies au moment de la compilation et ne sont pas modifiables.</span><span class="sxs-lookup"><span data-stu-id="8a998-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="8a998-104">Utilisez des constantes pour fournir des noms explicites au lieu de littéraux numériques (« nombres magiques ») pour les valeurs spéciales.</span><span class="sxs-lookup"><span data-stu-id="8a998-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a998-105">En C#, la directive de préprocesseur [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) ne peut pas être utilisée pour définir des constantes de la manière généralement utilisée en C et C++.</span><span class="sxs-lookup"><span data-stu-id="8a998-105">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="8a998-106">Pour définir des valeurs constantes de types intégraux (`int`, `byte`, etc.), utilisez un type énuméré.</span><span class="sxs-lookup"><span data-stu-id="8a998-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="8a998-107">Pour plus d’informations, consultez [enum](../../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="8a998-107">For more information, see [enum](../../language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="8a998-108">Pour définir des constantes non intégrales, une approche consiste à les regrouper dans une classe statique unique nommée `Constants`.</span><span class="sxs-lookup"><span data-stu-id="8a998-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="8a998-109">Cette opération exige que toutes les références aux constantes soient précédées par le nom de classe, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8a998-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a998-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="8a998-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="8a998-111">L’utilisation du qualificateur de nom de classe permet de garantir que les personnes qui utilisent la constante, dont vous-même, comprennent qu’il s’agit d’une valeur constante et qu’elle ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="8a998-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a998-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a998-112">See also</span></span>

- [<span data-ttu-id="8a998-113">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="8a998-113">Classes and Structs</span></span>](./index.md)
