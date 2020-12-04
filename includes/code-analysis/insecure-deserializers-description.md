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
Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. Une attaque contre un désérialiseur non sécurisé peut, par exemple, exécuter des commandes sur le système d’exploitation sous-jacent, communiquer sur le réseau ou supprimer des fichiers.
