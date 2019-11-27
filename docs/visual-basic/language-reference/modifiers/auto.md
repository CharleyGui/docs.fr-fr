---
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351615"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="a50a6-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a50a6-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="a50a6-103">Spécifie que Visual Basic doit marshaler des chaînes d’après les règles de .NET Framework en fonction du nom externe de la procédure externe déclarée.</span><span class="sxs-lookup"><span data-stu-id="a50a6-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="a50a6-104">Quand vous appelez une procédure définie à l’extérieur de votre projet, le compilateur Visual Basic n’a pas accès aux informations qu’il doit avoir pour appeler correctement la procédure.</span><span class="sxs-lookup"><span data-stu-id="a50a6-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="a50a6-105">Ces informations incluent l’emplacement de la procédure, son identification, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise.</span><span class="sxs-lookup"><span data-stu-id="a50a6-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="a50a6-106">L' [instruction DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="a50a6-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="a50a6-107">La partie `charsetmodifier` de l’instruction `Declare` fournit les informations de jeu de caractères pour le marshaling des chaînes lors d’un appel à la procédure externe.</span><span class="sxs-lookup"><span data-stu-id="a50a6-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="a50a6-108">Cela affecte également la manière dont Visual Basic recherche le nom de la procédure externe dans le fichier externe.</span><span class="sxs-lookup"><span data-stu-id="a50a6-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="a50a6-109">Le modificateur de `Auto` spécifie que Visual Basic doit marshaler des chaînes d’après les règles d' .NET Framework et qu’il doit déterminer le jeu de caractères de base de la plateforme d’exécution et éventuellement modifier le nom de la procédure externe en cas d’échec de la recherche initiale.</span><span class="sxs-lookup"><span data-stu-id="a50a6-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="a50a6-110">Pour plus d’informations, consultez « Jeux de caractères » dans l' [instruction DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a50a6-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="a50a6-111">Si aucun modificateur de jeu de caractères n’est spécifié, `Ansi` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a50a6-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a50a6-112">Notes</span><span class="sxs-lookup"><span data-stu-id="a50a6-112">Remarks</span></span>  
 <span data-ttu-id="a50a6-113">Le modificateur `Auto` peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="a50a6-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a50a6-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="a50a6-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="a50a6-115">Notes de développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="a50a6-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="a50a6-116">Ce mot clé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a50a6-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a50a6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a50a6-117">See also</span></span>

- [<span data-ttu-id="a50a6-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="a50a6-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="a50a6-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="a50a6-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="a50a6-120">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a50a6-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
