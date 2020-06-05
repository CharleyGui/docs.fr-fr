---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 67792e52c21555bef46548e9ab0a6ebd32061071
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373198"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="0fd32-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fd32-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="0fd32-103">Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs American National Standards Institute (ANSI), quel que soit le nom de la procédure externe déclarée.</span><span class="sxs-lookup"><span data-stu-id="0fd32-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="0fd32-104">Quand vous appelez une procédure définie à l’extérieur de votre projet, le compilateur Visual Basic n’a pas accès aux informations dont il a besoin pour appeler correctement la procédure.</span><span class="sxs-lookup"><span data-stu-id="0fd32-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="0fd32-105">Ces informations incluent l’emplacement de la procédure, son identification, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise.</span><span class="sxs-lookup"><span data-stu-id="0fd32-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="0fd32-106">L' [instruction DECLARE](../statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="0fd32-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="0fd32-107">La `charsetmodifier` partie de l' `Declare` instruction fournit les informations de jeu de caractères pour le marshaling des chaînes lors d’un appel à la procédure externe.</span><span class="sxs-lookup"><span data-stu-id="0fd32-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="0fd32-108">Cela affecte également la manière dont Visual Basic recherche le nom de la procédure externe dans le fichier externe.</span><span class="sxs-lookup"><span data-stu-id="0fd32-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="0fd32-109">Le `Ansi` modificateur spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs ANSI et rechercher la procédure sans modifier son nom au cours de la recherche.</span><span class="sxs-lookup"><span data-stu-id="0fd32-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="0fd32-110">Si aucun modificateur de jeu de caractères n’est spécifié, `Ansi` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0fd32-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fd32-111">Notes</span><span class="sxs-lookup"><span data-stu-id="0fd32-111">Remarks</span></span>  
 <span data-ttu-id="0fd32-112">Le `Ansi` modificateur peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="0fd32-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="0fd32-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="0fd32-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="0fd32-114">Notes de développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="0fd32-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="0fd32-115">Ce mot clé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0fd32-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd32-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fd32-116">See also</span></span>

- [<span data-ttu-id="0fd32-117">Auto</span><span class="sxs-lookup"><span data-stu-id="0fd32-117">Auto</span></span>](auto.md)
- [<span data-ttu-id="0fd32-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="0fd32-118">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="0fd32-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0fd32-119">Keywords</span></span>](../keywords/index.md)
