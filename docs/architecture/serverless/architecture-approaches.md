---
title: Approches d’architecture - Applications sans serveur
description: Une introduction aux approches d’architecture pour la construction d’applications d’entreprise basées sur le cloud, des architectures de niveau N aux sans serveur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522895"
---
# <a name="architecture-approaches"></a>Approches de l’architecture

Comprendre les approches existantes pour l’architecture des applications d’entreprise aide à clarifier le rôle joué par serverless. Il existe de nombreuses approches et modèles qui ont évolué au fil des décennies de développement de logiciels, et tous ont leurs propres avantages et inconvénients. Dans de nombreux cas, la solution ultime peut ne pas impliquer de décider d’une seule approche, mais peut intégrer plusieurs approches. Les scénarios de migration impliquent souvent le passage d’une approche d’architecture à une autre par une approche hybride.

Ce chapitre donne un aperçu des modèles d’architecture logique et physique pour les applications d’entreprise.

## <a name="architecture-patterns"></a>Modèles d’architecture

Les applications commerciales modernes suivent une variété de modèles d’architecture. Cette section représente une étude des tendances communes. Les modèles énumérés ici ne sont pas nécessairement toutes les meilleures pratiques, mais illustrent des approches différentes.

Pour plus d’informations, consultez [le guide d’architecture d’application Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monolithes

Beaucoup d’applications d’affaires suivent un modèle de monolithe. Les applications héritées sont souvent mises en œuvre comme monolithes. Dans le modèle de monolithe, toutes les préoccupations d’application sont contenues dans un déploiement unique. Tout, de l’interface utilisateur aux appels de base de données, est inclus dans la même base de code.

![Architecture monolithique](./media/monolith-architecture.png)

Il y a plusieurs avantages à l’approche monolithe. Il est souvent facile de tirer vers le bas une base de code unique et commencer à travailler. Le temps de montée en puissance peut être moins élevé, et la création d’environnements de test est aussi simple que de fournir une nouvelle copie. Le monolithe peut être conçu pour inclure plusieurs composants et applications.

Malheureusement, le motif monolithe a tendance à se décomposer à l’échelle. Les principaux inconvénients de l’approche monolithique sont les suivants :

- Difficile de travailler en parallèle dans la même base de code.
- Tout changement, aussi insignifiant soit-il, nécessite le déploiement d’une nouvelle version de l’ensemble de l’application.
- La refactoration pourrait avoir des répercussions sur l’ensemble de l’application.
- Souvent, la seule solution à l’échelle est de créer de multiples copies à forte intensité de ressources du monolithe.
- À mesure que les systèmes se développent ou que d’autres systèmes sont acquis, l’intégration peut être difficile.
- Il peut être difficile à tester en raison de la nécessité de configurer l’ensemble du monolithe.
- La réutilisation du code est difficile et souvent d’autres applications finissent par avoir leurs propres copies de code.

Beaucoup d’entreprises se tournent vers le cloud comme une occasion de migrer les applications monolithes et en même temps les refactorisent vers des modèles plus utilisables. Il est courant d’éliminer les applications et composants individuels pour leur permettre d’être maintenus, déployés et mis à l’échelle séparément.

## <a name="n-layer-applications"></a>Applications N-Layer

Logique d’application de partition de couche N en couches spécifiques. Les couches les plus courantes sont les suivantes :

- Interface utilisateur
- Logique métier
- Accès aux données

D’autres couches peuvent inclure middleware, traitement par lots, et API. Il est important de noter que les couches sont logiques. Bien qu’ils soient développés isolément, ils peuvent tous être déployés sur la même plate-forme cible.

![Architecture N-Layer](./media/n-layer-architecture.png)

L’approche N-Layer présente plusieurs avantages, notamment :

- La refactoration est isolée jusqu’à une couche.
- Les équipes peuvent construire, tester, déployer et maintenir indépendamment des couches séparées.
- Les couches peuvent être échangées, par exemple la couche de données peut accéder à plusieurs bases de données sans nécessiter de modifications de la couche d’interface utilisateur.

Serverless peut être utilisé pour implémenter une ou plusieurs couches.

## <a name="microservices"></a>Microservices

**[Les architectures de microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** contiennent des caractéristiques communes qui comprennent :

- Les applications sont composées de plusieurs petits services.
- Chaque service fonctionne dans son propre processus.
- Les services sont alignés sur les domaines d’activité.
- Les services communiquent sur les API légères, généralement en utilisant HTTP comme transport.
- Les services peuvent être déployés et mis à niveau indépendamment.
- Les services ne dépendent pas d’un seul magasin de données.
- Le système est conçu avec l’échec à l’esprit, et l’application peut encore fonctionner même lorsque certains services échouent.

Les microservices n’ont pas besoin d’être mutuellement exclusifs à d’autres approches d’architecture. Par exemple, une architecture N-Tier peut utiliser des microservices pour le niveau intermédiaire. Il est également possible d’implémenter des microservices de diverses façons, des répertoires virtuels sur les hôtes DE l’IIS aux conteneurs. Les caractéristiques des microservices les rendent particulièrement idéales pour les implémentations sans serveur.

![Architecture de microservices](./media/microservices-architecture.png)

Les avantages des architectures de microservices incluent :

- La refactoration est souvent isolée à un seul service.
- Les services peuvent être mis à niveau indépendamment les uns des autres.
- La résilience et l’élasticité peuvent être réglées aux exigences des services individuels.
- Le développement peut se faire en parallèle entre des équipes et des plates-formes disparates.
- Il est plus facile d’écrire des tests complets pour des services isolés.

Les microservices présentent leurs propres défis, notamment :

- Déterminer quels services sont disponibles et comment les appeler.
- Gérer le cycle de vie des services.
- Comprendre comment les services s’intègrent dans l’application globale.
- Test complet du système des appels effectués dans des services disparates.

En fin de compte, il existe des solutions pour relever tous ces défis, y compris en puisant dans les avantages de serverless qui sont discutés plus tard.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](architecture-deployment-approaches.md)
