---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 7ef31a188e1564da47ea1e7323cdd4cd5ef5be60
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236674"
---
# <a name="msmq"></a><span data-ttu-id="4228b-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="4228b-102">MSMQ</span></span>

<span data-ttu-id="4228b-103">Dans une application MSMQ, aucune activité supplémentaire n'est transférée du canal mis en file d'attente vers MSMQ et de MSMQ vers le canal mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="4228b-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="4228b-104">De plus, l'ID de message MSMQ et l'ID de message SOAP (ainsi que l'ID d'activité, s'il existe) sont suivis dans le cadre des suivis de canaux mis en file d'attente lors d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="4228b-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="4228b-105">L'ID de message MSMQ et l'ID de message SOAP (ainsi que l'ID d'activité, s'il existe) sont suivis dans le cadre des suivis de canaux mis en file d'attente lors d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="4228b-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="4228b-106">Les transferts requis sur l’opération de réception sont exécutés de la même façon que n’importe quel autre transport (recevoir des octets->opération traiter le message->).</span><span class="sxs-lookup"><span data-stu-id="4228b-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
