---
title: Le type de la valeur facultative pour le paramètre optionnel <parametername> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 8e53d036ead114d828d9035cef76cee72bf6b1db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400290"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="34c5d-102">Le type de la valeur facultative pour le paramètre optionnel \<parametername> n'est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="34c5d-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>
<span data-ttu-id="34c5d-103">Une procédure est marquée comme `<CLSCompliant(True)>` mais déclare un paramètre [facultatif](../modifiers/optional.md) avec la valeur par défaut d’un type non conforme.</span><span class="sxs-lookup"><span data-stu-id="34c5d-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="34c5d-104">Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md)), elle doit utiliser uniquement des types conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="34c5d-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="34c5d-105">Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales.</span><span class="sxs-lookup"><span data-stu-id="34c5d-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="34c5d-106">Elle s’applique également aux valeurs par défaut des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="34c5d-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="34c5d-107">Les types de données Visual Basics suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="34c5d-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="34c5d-108">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="34c5d-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="34c5d-109">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="34c5d-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="34c5d-110">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="34c5d-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="34c5d-111">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="34c5d-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="34c5d-112">Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité.</span><span class="sxs-lookup"><span data-stu-id="34c5d-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="34c5d-113">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="34c5d-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="34c5d-114">Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.</span><span class="sxs-lookup"><span data-stu-id="34c5d-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="34c5d-115">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="34c5d-115">By default, this message is a warning.</span></span> <span data-ttu-id="34c5d-116">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="34c5d-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="34c5d-117">**ID d’erreur :** BC40042</span><span class="sxs-lookup"><span data-stu-id="34c5d-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="34c5d-118">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="34c5d-118">To correct this error</span></span>  
  
- <span data-ttu-id="34c5d-119">Si le paramètre facultatif doit avoir une valeur par défaut de ce type particulier, supprimez <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="34c5d-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="34c5d-120">La procédure ne peut pas être conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="34c5d-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="34c5d-121">Si la procédure doit être conforme à CLS, remplacez le type de cette valeur par défaut par le type conforme à CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="34c5d-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="34c5d-122">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="34c5d-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="34c5d-123">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="34c5d-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="34c5d-124">Si vous utilisez des objets Automation ou COM, gardez à l’esprit que certains types ont des largeurs de données différentes de celles de la .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34c5d-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="34c5d-125">Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="34c5d-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="34c5d-126">Si vous acceptez un entier 16 bits d’un tel composant, déclarez-le comme `Short` au lieu de `Integer` dans votre code Visual Basic managé.</span><span class="sxs-lookup"><span data-stu-id="34c5d-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
