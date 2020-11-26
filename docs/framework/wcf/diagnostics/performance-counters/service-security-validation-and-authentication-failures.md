---
title: 'Service : nombre d’échecs de la validation de la sécurité et de l’authentification'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: d89419d7d579d29a1c57370d61eefb8b26333a40
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236856"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="1df32-102">Service : nombre d’échecs de la validation de la sécurité et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="1df32-102">Service: Security Validation and Authentication Failures</span></span>

<span data-ttu-id="1df32-103">Nom de compteur : nombre d’échecs de la validation de la sécurité et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="1df32-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="1df32-104">Description</span><span class="sxs-lookup"><span data-stu-id="1df32-104">Description</span></span>  

 <span data-ttu-id="1df32-105">Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="1df32-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="1df32-106">Ces problèmes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="1df32-106">Such problems include:</span></span>  
  
- <span data-ttu-id="1df32-107">Impossibilité de lire le jeton client depuis le message.</span><span class="sxs-lookup"><span data-stu-id="1df32-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="1df32-108">Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).</span><span class="sxs-lookup"><span data-stu-id="1df32-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="1df32-109">Échec de la vérification de signature (par exemple, falsification du message).</span><span class="sxs-lookup"><span data-stu-id="1df32-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="1df32-110">Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.</span><span class="sxs-lookup"><span data-stu-id="1df32-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="1df32-111">Impossibilité de déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="1df32-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="1df32-112">Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).</span><span class="sxs-lookup"><span data-stu-id="1df32-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="1df32-113">Erreurs lors de la négociation TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="1df32-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
