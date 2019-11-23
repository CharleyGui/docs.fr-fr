---
title: Opérateur GetType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592151"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="b7bb1-102">Opérateur GetType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7bb1-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="b7bb1-103">Retourne un objet <xref:System.Type> pour le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="b7bb1-104">L’objet <xref:System.Type> fournit des informations sur le type, telles que ses propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bb1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7bb1-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7bb1-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="b7bb1-106">Parameters</span></span>  
  
|<span data-ttu-id="b7bb1-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b7bb1-107">Parameter</span></span>|<span data-ttu-id="b7bb1-108">Description</span><span class="sxs-lookup"><span data-stu-id="b7bb1-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="b7bb1-109">Nom du type pour lequel vous souhaitez obtenir des informations.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7bb1-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="b7bb1-110">Remarks</span></span>  
 <span data-ttu-id="b7bb1-111">L’opérateur `GetType` retourne l’objet <xref:System.Type> pour le `typename`spécifié.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="b7bb1-112">Vous pouvez passer le nom de n’importe quel type défini dans `typename`.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="b7bb1-113">Ce dernier est détaillé ci-après :</span><span class="sxs-lookup"><span data-stu-id="b7bb1-113">This includes the following:</span></span>  
  
- <span data-ttu-id="b7bb1-114">Tout Visual Basic type de données, tel que `Boolean` ou `Date`.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="b7bb1-115">Tout .NET Framework classe, structure, module ou interface, comme <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="b7bb1-116">Toute classe, structure, module ou interface définie par votre application.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="b7bb1-117">Tout tableau défini par votre application.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="b7bb1-118">Tout délégué défini par votre application.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="b7bb1-119">Toute énumération définie par Visual Basic, le .NET Framework ou votre application.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="b7bb1-120">Si vous souhaitez obtenir l’objet de type d’une variable objet, utilisez la méthode <xref:System.Type.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b7bb1-121">L’opérateur `GetType` peut être utile dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7bb1-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="b7bb1-122">Vous devez accéder aux métadonnées d’un type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="b7bb1-123">L’objet <xref:System.Type> fournit des métadonnées, telles que des membres de type et des informations de déploiement.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="b7bb1-124">Vous en aurez besoin, par exemple, pour réfléchir un assembly.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="b7bb1-125">Pour plus d'informations, consultez <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="b7bb1-126">Vous souhaitez comparer deux références d’objet pour voir si elles font référence à des instances du même type.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="b7bb1-127">Si c’est le cas, `GetType` retourne des références au même objet <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7bb1-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7bb1-128">Example</span></span>  
 <span data-ttu-id="b7bb1-129">Les exemples suivants illustrent l’opérateur `GetType` en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="b7bb1-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="b7bb1-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7bb1-130">See also</span></span>

- [<span data-ttu-id="b7bb1-131">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7bb1-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b7bb1-132">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="b7bb1-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b7bb1-133">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="b7bb1-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
