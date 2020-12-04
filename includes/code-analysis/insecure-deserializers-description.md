---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 9235f1bcda7529b71aef542d3a49da08a9d4b59e
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586683"
---
<span data-ttu-id="11c75-101">Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées.</span><span class="sxs-lookup"><span data-stu-id="11c75-101">Insecure deserializers are vulnerable when deserializing untrusted data.</span></span> <span data-ttu-id="11c75-102">Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants.</span><span class="sxs-lookup"><span data-stu-id="11c75-102">An attacker could modify the serialized data to include unexpected types to inject objects with malicious side effects.</span></span> <span data-ttu-id="11c75-103">Une attaque contre un désérialiseur non sécurisé peut, par exemple, exécuter des commandes sur le système d’exploitation sous-jacent, communiquer sur le réseau ou supprimer des fichiers.</span><span class="sxs-lookup"><span data-stu-id="11c75-103">An attack against an insecure deserializer could, for example, execute commands on the underlying operating system, communicate over the network, or delete files.</span></span>
