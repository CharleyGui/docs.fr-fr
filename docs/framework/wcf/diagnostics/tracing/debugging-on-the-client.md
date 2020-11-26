---
title: Débogage sur le client
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 4fc647bcde3d9aed27a46298be8d863947ba0726
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243987"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="a7898-102">Débogage sur le client</span><span class="sxs-lookup"><span data-stu-id="a7898-102">Debugging on the Client</span></span>

<span data-ttu-id="a7898-103">Pour permettre aux utilisateurs d’écrire plus facilement des applications clientes pour votre service WCF, vous pouvez ajouter le [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) comportement de service au fichier de configuration de votre service.</span><span class="sxs-lookup"><span data-stu-id="a7898-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="a7898-104">Ce comportement permet de publier des pages d'aide et de retourner des informations d'exception gérées dans les détails des erreurs SOAP renvoyées au client.</span><span class="sxs-lookup"><span data-stu-id="a7898-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
