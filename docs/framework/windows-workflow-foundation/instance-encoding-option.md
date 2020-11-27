---
title: Option d'encodage d'instance
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 416394eb346a7c82385da32a89bd54179b255cd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279894"
---
# <a name="instance-encoding-option"></a>Option d'encodage d'instance

La propriété **option d’encodage d’instance** du magasin d’instances de workflow SQL vous permet de spécifier si le fournisseur de persistance SQL doit compresser les informations d’état de l’instance de workflow à l’aide de l’algorithme gzip avant d’enregistrer les informations dans la base de données de persistance. Les valeurs autorisées pour cette propriété sont : Gzip et Aucun. La valeur par défaut est Aucun. La liste suivante décrit ces trois options.  
  
1. **Gzip**. Le fournisseur de persistance encode les informations d'état à l'aide de l'algorithme Gzip avant de rendre les informations d'état persistantes dans la base de données de persistance.  
  
2. **Aucun**. Le fournisseur de persistance n'encode pas les informations d'état avant d'enregistrer les informations dans la base de données de persistance.  
  
 L'encodage des informations de l'état de l'instance du workflow à l'aide du Gzip réduit la consommation de mémoire dans la base de données SQL ainsi que la consommation réseau si la base de données réside sur un autre ordinateur sur le réseau différent de l'ordinateur sur lequel l'hôte du service de workflow s'exécute. Une recommandation générale consiste à définir la propriété de l' **option d’encodage d’instance** sur **None** si l’état de l’instance de workflow est petit.
