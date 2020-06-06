---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704360"
---
# \<commonBehaviors>
<span data-ttu-id="7b3a1-101">La section `commonBehaviors` peut uniquement être définie dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="7b3a1-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="7b3a1-102">Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="7b3a1-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="7b3a1-103">Chaque collection définit des éléments de comportement consommés respectivement par tous les services et points de terminaison WCF sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7b3a1-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="7b3a1-104">Les comportements définis dans `endpointBehaviors` sont appliqués uniquement aux clients et les comportements définis dans `serviceBehaviors` s'appliquent uniquement aux services.</span><span class="sxs-lookup"><span data-stu-id="7b3a1-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="7b3a1-105">Si un comportement est défini dans les sections `commonBehaviors` et `behaviors`, le comportement dans la section `behaviors` a la préférence.</span><span class="sxs-lookup"><span data-stu-id="7b3a1-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
