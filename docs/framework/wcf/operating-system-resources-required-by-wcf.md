---
title: Ressources de système d'exploitation requises par WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961137"
---
# <a name="operating-system-resources-required-by-wcf"></a>Ressources de système d'exploitation requises par WCF

Windows Communication Foundation (WCF) dépend de plusieurs ressources fournies par le système d’exploitation pour fonctionner. Le tableau suivant répertorie ces ressources :

|Ressource|Description|
|--------------|-----------------|
|Microsoft Distributed Transaction Coordinator (MSDTC)|Requis pour prendre en charge les transactions OleTx.|
|Services IIS (Internet Information Services)|Requis si vous souhaitez utiliser les services Internet (IIS) pour héberger votre application.|
|Windows Process Activation Service (WAS)|Requis si vous souhaitez utiliser les services WAS pour héberger votre application.|
