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
ms.openlocfilehash: 799a7320b701384dc5f4b4b46fef8544f6b15b02
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875508"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="b9188-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9188-102">Auto (Visual Basic)</span></span>

<span data-ttu-id="b9188-103">Spécifie que Visual Basic doit marshaler des chaînes d’après les règles de .NET Framework en fonction du nom externe de la procédure externe déclarée.</span><span class="sxs-lookup"><span data-stu-id="b9188-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="b9188-104">Quand vous appelez une procédure définie à l’extérieur de votre projet, le compilateur Visual Basic n’a pas accès aux informations qu’il doit avoir pour appeler correctement la procédure.</span><span class="sxs-lookup"><span data-stu-id="b9188-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="b9188-105">Ces informations incluent l’emplacement de la procédure, son identification, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise.</span><span class="sxs-lookup"><span data-stu-id="b9188-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="b9188-106">L' [instruction DECLARE](../statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b9188-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="b9188-107">La `charsetmodifier` partie de l' `Declare` instruction fournit les informations de jeu de caractères pour le marshaling des chaînes lors d’un appel à la procédure externe.</span><span class="sxs-lookup"><span data-stu-id="b9188-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="b9188-108">Cela affecte également la manière dont Visual Basic recherche le nom de la procédure externe dans le fichier externe.</span><span class="sxs-lookup"><span data-stu-id="b9188-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="b9188-109">Le `Auto` modificateur spécifie que Visual Basic doit marshaler les chaînes en fonction des règles de .NET Framework, et qu’il doit déterminer le jeu de caractères de base de la plateforme d’exécution et éventuellement modifier le nom de la procédure externe en cas d’échec de la recherche initiale.</span><span class="sxs-lookup"><span data-stu-id="b9188-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="b9188-110">Pour plus d’informations, consultez « Jeux de caractères » dans l' [instruction DECLARE](../statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b9188-110">For more information, see "Character Sets" in [Declare Statement](../statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="b9188-111">Si aucun modificateur de jeu de caractères n’est spécifié, `Ansi` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b9188-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9188-112">Notes</span><span class="sxs-lookup"><span data-stu-id="b9188-112">Remarks</span></span>  

 <span data-ttu-id="b9188-113">Le `Auto` modificateur peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="b9188-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b9188-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="b9188-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="b9188-115">Notes de développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="b9188-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="b9188-116">Ce mot clé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b9188-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9188-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9188-117">See also</span></span>

- [<span data-ttu-id="b9188-118">Caractères</span><span class="sxs-lookup"><span data-stu-id="b9188-118">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="b9188-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="b9188-119">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="b9188-120">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b9188-120">Keywords</span></span>](../keywords/index.md)
