---
title: Le type de retour de la fonction '<procedurename>' n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 9cc7e25ef1be21ff2f6a71dcb61bc29ec92da30f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400355"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="cd3cf-102">Le type de retour de la fonction '\<procedurename>' n'est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="cd3cf-102">Return type of function '\<procedurename>' is not CLS-compliant</span></span>
<span data-ttu-id="cd3cf-103">Une `Function` procédure est marquée comme `<CLSCompliant(True)>` mais retourne un type qui est marqué comme `<CLSCompliant(False)>` , qui n’est pas marqué ou qui n’est pas qualifié car il s’agit d’un type non conforme.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="cd3cf-104">Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md)), elle doit utiliser uniquement des types conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="cd3cf-105">Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="cd3cf-106">Les types de données Visual Basics suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="cd3cf-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="cd3cf-107">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="cd3cf-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="cd3cf-108">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="cd3cf-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="cd3cf-109">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="cd3cf-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="cd3cf-110">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="cd3cf-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="cd3cf-111">Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="cd3cf-112">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="cd3cf-113">Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="cd3cf-114">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-114">By default, this message is a warning.</span></span> <span data-ttu-id="cd3cf-115">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cd3cf-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="cd3cf-116">**ID d’erreur :** BC40027</span><span class="sxs-lookup"><span data-stu-id="cd3cf-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd3cf-117">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="cd3cf-117">To correct this error</span></span>  
  
- <span data-ttu-id="cd3cf-118">Si la `Function` procédure doit retourner ce type particulier, supprimez <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cd3cf-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="cd3cf-119">La procédure ne peut pas être conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="cd3cf-120">Si la `Function` procédure doit être conforme CLS, remplacez le type de retour par le type conforme CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="cd3cf-121">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="cd3cf-122">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="cd3cf-123">Si vous utilisez des objets Automation ou COM, gardez à l’esprit que certains types ont des largeurs de données différentes de celles de la .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="cd3cf-124">Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="cd3cf-125">Si vous retournez un entier 16 bits à un tel composant, déclarez-le comme `Short` au lieu de `Integer` dans votre code Visual Basic managé.</span><span class="sxs-lookup"><span data-stu-id="cd3cf-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
