---
title: Nombre d'échecs de validation de la sécurité et d'authentification par seconde
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 7d680e9a5b03943fdec212c509b6d80a2d60246c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559133"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="f5f1d-102">Nombre d'échecs de validation de la sécurité et d'authentification par seconde</span><span class="sxs-lookup"><span data-stu-id="f5f1d-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="f5f1d-103">Nom du compteur : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde.</span><span class="sxs-lookup"><span data-stu-id="f5f1d-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f5f1d-104">Description</span><span class="sxs-lookup"><span data-stu-id="f5f1d-104">Description</span></span>  
 <span data-ttu-id="f5f1d-105">Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="f5f1d-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="f5f1d-106">Ces problèmes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f5f1d-106">Such problems include:</span></span>  
  
- <span data-ttu-id="f5f1d-107">Impossibilité de lire le jeton client depuis le message.</span><span class="sxs-lookup"><span data-stu-id="f5f1d-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="f5f1d-108">Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).</span><span class="sxs-lookup"><span data-stu-id="f5f1d-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="f5f1d-109">Échec de la vérification de signature (par exemple, falsification du message).</span><span class="sxs-lookup"><span data-stu-id="f5f1d-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="f5f1d-110">Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.</span><span class="sxs-lookup"><span data-stu-id="f5f1d-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="f5f1d-111">Impossibilité de déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="f5f1d-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="f5f1d-112">Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).</span><span class="sxs-lookup"><span data-stu-id="f5f1d-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="f5f1d-113">Erreurs lors de la négociation TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="f5f1d-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="f5f1d-114">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante :</span><span class="sxs-lookup"><span data-stu-id="f5f1d-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="f5f1d-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="f5f1d-115">(N1-N0)/((D1-D0)/F)</span></span>
