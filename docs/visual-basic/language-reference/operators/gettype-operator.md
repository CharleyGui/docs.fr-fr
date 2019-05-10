---
title: Opérateur GetType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 3366a0d1a90667cf1d9b58b211892ad264849c59
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633244"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="6e68a-102">Opérateur GetType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e68a-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="6e68a-103">Retourne un <xref:System.Type> objet pour le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="6e68a-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="6e68a-104">Le <xref:System.Type> objet fournit des informations sur le type telles que ses propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="6e68a-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e68a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e68a-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e68a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e68a-106">Parameters</span></span>  
  
|<span data-ttu-id="6e68a-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6e68a-107">Parameter</span></span>|<span data-ttu-id="6e68a-108">Description</span><span class="sxs-lookup"><span data-stu-id="6e68a-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="6e68a-109">Le nom du type pour lequel vous souhaitez des informations.</span><span class="sxs-lookup"><span data-stu-id="6e68a-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e68a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="6e68a-110">Remarks</span></span>  
 <span data-ttu-id="6e68a-111">Le `GetType` opérateur retourne le <xref:System.Type> objet spécifié `typename`.</span><span class="sxs-lookup"><span data-stu-id="6e68a-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="6e68a-112">Vous pouvez passer le nom de n’importe quel type défini dans `typename`.</span><span class="sxs-lookup"><span data-stu-id="6e68a-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="6e68a-113">Ce dernier est détaillé ci-après :</span><span class="sxs-lookup"><span data-stu-id="6e68a-113">This includes the following:</span></span>  
  
- <span data-ttu-id="6e68a-114">Type de données Visual Basic, tel que `Boolean` ou `Date`.</span><span class="sxs-lookup"><span data-stu-id="6e68a-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="6e68a-115">Toute classe .NET Framework, structure, module ou interface, tel que <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e68a-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="6e68a-116">Toute classe, structure, module ou interface définie par votre application.</span><span class="sxs-lookup"><span data-stu-id="6e68a-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="6e68a-117">N’importe quel tableau définie par votre application.</span><span class="sxs-lookup"><span data-stu-id="6e68a-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="6e68a-118">Tout délégué défini par votre application.</span><span class="sxs-lookup"><span data-stu-id="6e68a-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="6e68a-119">Toute énumération définie par Visual Basic, le .NET Framework ou votre application.</span><span class="sxs-lookup"><span data-stu-id="6e68a-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="6e68a-120">Si vous souhaitez obtenir l’objet de type d’une variable objet, utilisez le <xref:System.Type.GetType%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6e68a-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6e68a-121">Le `GetType` opérateur peut être utile dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="6e68a-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="6e68a-122">Vous devez accéder à des métadonnées pour un type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6e68a-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="6e68a-123">Le <xref:System.Type> objet qui fournit des métadonnées telles que les membres de type et des informations sur le déploiement.</span><span class="sxs-lookup"><span data-stu-id="6e68a-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="6e68a-124">Vous devez, par exemple, pour refléter sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="6e68a-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="6e68a-125">Pour plus d'informations, consultez <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e68a-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="6e68a-126">Vous souhaitez comparer deux références d’objet pour voir si elles font référence aux instances du même type.</span><span class="sxs-lookup"><span data-stu-id="6e68a-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="6e68a-127">S’ils le font, `GetType` retourne des références au même <xref:System.Type> objet.</span><span class="sxs-lookup"><span data-stu-id="6e68a-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e68a-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e68a-128">Example</span></span>  
 <span data-ttu-id="6e68a-129">Les exemples suivants illustrent le `GetType` opérateur en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="6e68a-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="6e68a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e68a-130">See also</span></span>

- [<span data-ttu-id="6e68a-131">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e68a-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6e68a-132">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="6e68a-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="6e68a-133">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="6e68a-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
