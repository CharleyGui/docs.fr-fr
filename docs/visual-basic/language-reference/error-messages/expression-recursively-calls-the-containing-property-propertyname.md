---
title: L'expression appelle de manière récursive la propriété conteneur '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698566"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="65fea-102">L’expression appelle de manière récursive la propriété conteneur' \<propertyname > '</span><span class="sxs-lookup"><span data-stu-id="65fea-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="65fea-103">Une instruction dans la procédure `Set` d’une définition de propriété stocke une valeur dans le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="65fea-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="65fea-104">L’approche recommandée pour conserver la valeur d’une propriété consiste à définir une variable `Private` dans le conteneur de la propriété et à l’utiliser à la fois dans les procédures `Get` et `Set`.</span><span class="sxs-lookup"><span data-stu-id="65fea-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="65fea-105">La procédure `Set` doit ensuite stocker la valeur entrante dans cette variable `Private`.</span><span class="sxs-lookup"><span data-stu-id="65fea-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="65fea-106">La procédure `Get` se comporte comme une procédure `Function`, de sorte qu’elle peut attribuer une valeur au nom de la propriété et retourner le contrôle en rencontrant l’instruction `End Get`.</span><span class="sxs-lookup"><span data-stu-id="65fea-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="65fea-107">Toutefois, l’approche recommandée consiste à inclure la variable `Private` comme valeur dans une [instruction return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="65fea-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="65fea-108">La procédure `Set` se comporte comme une procédure `Sub`, qui ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="65fea-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="65fea-109">Par conséquent, le nom de la procédure ou de la propriété n’a aucune signification particulière dans une procédure `Set`, et vous ne pouvez pas y stocker de valeur.</span><span class="sxs-lookup"><span data-stu-id="65fea-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="65fea-110">L’exemple suivant illustre l’approche qui peut provoquer cette erreur, suivie de l’approche recommandée.</span><span class="sxs-lookup"><span data-stu-id="65fea-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```vb  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 <span data-ttu-id="65fea-111">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="65fea-111">By default, this message is a warning.</span></span> <span data-ttu-id="65fea-112">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="65fea-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="65fea-113">**ID d’erreur :** BC42026</span><span class="sxs-lookup"><span data-stu-id="65fea-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65fea-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="65fea-114">To correct this error</span></span>  
  
- <span data-ttu-id="65fea-115">Réécrivez la définition de la propriété pour utiliser l’approche recommandée, comme illustré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="65fea-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fea-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65fea-116">See also</span></span>

- [<span data-ttu-id="65fea-117">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="65fea-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="65fea-118">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="65fea-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="65fea-119">Set (instruction)</span><span class="sxs-lookup"><span data-stu-id="65fea-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
