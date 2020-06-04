---
title: Dépannage des gestionnaires d’événements hérités
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 4e7bedd1de5197fcf8b69091f4cc878f41b01cd5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405104"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="17793-102">Dépannage des gestionnaires d'événements hérités dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17793-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="17793-103">Cette rubrique répertorie les problèmes courants qui surviennent avec les gestionnaires d’événements dans les composants hérités.</span><span class="sxs-lookup"><span data-stu-id="17793-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="17793-104">Procédures</span><span class="sxs-lookup"><span data-stu-id="17793-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="17793-105">Le code dans le gestionnaire d’événements s’exécute deux fois pour chaque appel</span><span class="sxs-lookup"><span data-stu-id="17793-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="17793-106">Un gestionnaire d’événements hérité ne doit pas inclure une clause [Handles](../../../language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="17793-106">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="17793-107">La méthode dans la classe de base est déjà associée à l’événement et est déclenchée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="17793-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="17793-108">Supprimez la `Handles` clause de la méthode héritée.</span><span class="sxs-lookup"><span data-stu-id="17793-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="17793-109">Si la méthode héritée n’a pas de `Handles` mot clé, vérifiez que votre code ne contient pas d' [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) supplémentaire ou d’autres méthodes qui gèrent le même événement.</span><span class="sxs-lookup"><span data-stu-id="17793-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17793-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17793-110">See also</span></span>

- [<span data-ttu-id="17793-111">Événements</span><span class="sxs-lookup"><span data-stu-id="17793-111">Events</span></span>](index.md)
