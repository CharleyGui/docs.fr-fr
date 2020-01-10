---
title: Création d'un modèle de chiffrement
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 00fff5f346633a9682d75cf6a3be7e8e7d5db7e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706290"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="0c609-102">Création d'un modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="0c609-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="0c609-103">Les composants de chiffrement de .NET Framework peuvent être combinés pour créer différents modèles permettant de chiffrer et de déchiffrer des données.</span><span class="sxs-lookup"><span data-stu-id="0c609-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="0c609-104">Un simple modèle de chiffrement pour chiffrer et déchiffrer des données peut spécifier les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c609-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="0c609-105">Chaque partie génère une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="0c609-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="0c609-106">Les parties échangent leurs clés publiques.</span><span class="sxs-lookup"><span data-stu-id="0c609-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="0c609-107">Chaque partie génère une clé secrète pour le chiffrement TripleDES (par exemple), et chiffre la clé nouvellement créée à l'aide de la clé publique de l'autre.</span><span class="sxs-lookup"><span data-stu-id="0c609-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="0c609-108">Chaque partie envoie les données à l'autre et combine la clé secrète de l'autre avec la sienne, dans un ordre spécifique, pour créer une clé secrète.</span><span class="sxs-lookup"><span data-stu-id="0c609-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="0c609-109">Les parties lancent ensuite une conversation à l'aide du chiffrement symétrique.</span><span class="sxs-lookup"><span data-stu-id="0c609-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="0c609-110">La création d’un modèle de chiffrement n’est pas une tâche facile.</span><span class="sxs-lookup"><span data-stu-id="0c609-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0c609-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c609-111">See also</span></span>

- [<span data-ttu-id="0c609-112">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="0c609-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
