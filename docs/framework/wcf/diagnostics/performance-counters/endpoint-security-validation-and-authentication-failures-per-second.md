---
title: 'Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: b2c5022caa5abe6154a3cb4dd4281dd212599b74
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256480"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="06a7f-102">Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde</span><span class="sxs-lookup"><span data-stu-id="06a7f-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="06a7f-103">Nom du compteur : Nombre d’échecs de validation de la sécurité et d’authentification par seconde</span><span class="sxs-lookup"><span data-stu-id="06a7f-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="06a7f-104">Description</span><span class="sxs-lookup"><span data-stu-id="06a7f-104">Description</span></span>  

 <span data-ttu-id="06a7f-105">Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="06a7f-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="06a7f-106">Ces problèmes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="06a7f-106">Such problems include:</span></span>  
  
- <span data-ttu-id="06a7f-107">Impossibilité de lire le jeton client depuis le message.</span><span class="sxs-lookup"><span data-stu-id="06a7f-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="06a7f-108">Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).</span><span class="sxs-lookup"><span data-stu-id="06a7f-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="06a7f-109">Échec de la vérification de signature (par exemple, falsification du message).</span><span class="sxs-lookup"><span data-stu-id="06a7f-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="06a7f-110">Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.</span><span class="sxs-lookup"><span data-stu-id="06a7f-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="06a7f-111">Impossibilité de déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="06a7f-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="06a7f-112">Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).</span><span class="sxs-lookup"><span data-stu-id="06a7f-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="06a7f-113">Erreurs lors de la négociation TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="06a7f-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="06a7f-114">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante :</span><span class="sxs-lookup"><span data-stu-id="06a7f-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="06a7f-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="06a7f-115">(N1-N0)/((D1-D0)/F)</span></span>
