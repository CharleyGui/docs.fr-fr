---
title: Action d'achèvement de l'instance
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044343"
---
# <a name="instance-completion-action"></a>Action d'achèvement de l'instance

La propriété **action d’achèvement** de l’instance du magasin d’instances de workflow SQL vous permet de spécifier si les données et métadonnées des instances de workflow sont supprimées de la base de données de persistance une fois les instances terminées. Les valeurs autorisées pour cette propriété sont **DeleteAll** et **DeleteNothing**. La liste suivante décrit ces trois options :

- **DeleteAll (valeur par défaut).** Si la valeur de la propriété est définie sur DeleteAll, les données et métadonnées d'instances de workflow sont supprimées de la base de données de persistance après que les instances ont abouti.

- **DeleteNothing.** Si la valeur de la propriété est définie sur DeleteNothing, les données et métadonnées d'instances de workflow sont conservées dans la base de données de persistance même après que les instances ont abouti.

  > [!CAUTION]
  > Garder les informations d'état de l'instance après que les instances ont abouti entraîne l'augmentation de la taille de la base de données de persistance. À mesure que la taille de la base de données augmente, les opérations de base de données que le sous-système de persistance effectue prennent plus de temps pour s'exécuter, donc vous devez régulièrement vider les informations d'état de l'instance de la base de données de persistance pour optimiser l'exécution de ces services.
