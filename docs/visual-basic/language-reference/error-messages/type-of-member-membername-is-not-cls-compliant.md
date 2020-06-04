---
title: Le type de membre '<membername>' n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 030cb31b8f1ba0e8eaa82eeb8e37153411a53404
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400303"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="6d453-102">Le type de membre '\<membername>' n'est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="6d453-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="6d453-103">Le type de données spécifié pour ce membre ne fait pas partie de l' [indépendance du langage et des composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="6d453-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="6d453-104">Il ne s’agit pas d’une erreur au sein de votre composant, car les .NET Framework et Visual Basic prennent en charge ce type de données.</span><span class="sxs-lookup"><span data-stu-id="6d453-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="6d453-105">Toutefois, un autre composant écrit dans du code strictement conforme CLS peut ne pas prendre en charge ce type de données.</span><span class="sxs-lookup"><span data-stu-id="6d453-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="6d453-106">Un tel composant peut ne pas être en mesure d’interagir correctement avec votre composant.</span><span class="sxs-lookup"><span data-stu-id="6d453-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="6d453-107">Les types de données Visual Basics suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="6d453-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="6d453-108">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="6d453-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="6d453-109">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="6d453-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="6d453-110">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="6d453-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="6d453-111">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="6d453-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="6d453-112">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="6d453-112">By default, this message is a warning.</span></span> <span data-ttu-id="6d453-113">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6d453-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6d453-114">**ID d’erreur :** BC40025</span><span class="sxs-lookup"><span data-stu-id="6d453-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d453-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6d453-115">To correct this error</span></span>  
  
- <span data-ttu-id="6d453-116">Si votre composant ne s’interface qu’avec d’autres composants de .NET Framework ou n’interagit pas avec d’autres composants, vous n’avez pas besoin de modifier quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="6d453-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="6d453-117">Si vous interagissez avec un composant qui n’est pas écrit pour le .NET Framework, vous pouvez être en mesure de déterminer, soit par réflexion, soit à partir de la documentation, s’il prend en charge ce type de données.</span><span class="sxs-lookup"><span data-stu-id="6d453-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="6d453-118">Si c’est le cas, vous n’avez pas besoin de modifier quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="6d453-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="6d453-119">Si vous utilisez un composant qui ne prend pas en charge ce type de données, vous devez le remplacer par le type conforme CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="6d453-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="6d453-120">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="6d453-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="6d453-121">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="6d453-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="6d453-122">Si vous utilisez des objets Automation ou COM, gardez à l’esprit que certains types ont des largeurs de données différentes de celles de la .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d453-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="6d453-123">Par exemple, `uint` correspond souvent à 16 bits dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="6d453-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="6d453-124">Si vous passez un argument de 16 bits à un tel composant, déclarez-le comme `UShort` au lieu de `UInteger` dans votre code Visual Basic managé.</span><span class="sxs-lookup"><span data-stu-id="6d453-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d453-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d453-125">See also</span></span>

- [<span data-ttu-id="6d453-126">Réflexion</span><span class="sxs-lookup"><span data-stu-id="6d453-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
