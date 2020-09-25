---
title: Présentation de la sécurité
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: ede9b24828da74c043bed103595073c4607c51f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188991"
---
# <a name="security-overview"></a>Présentation de la sécurité

La sécurisation d'une application est un processus permanent. Un développeur ne peut à aucun moment garantir qu'une application est à l'abri de toute attaque car il est impossible de prédire les types d'attaques futures que les nouvelles technologies permettront de faire apparaître. Inversement, le fait que personne n'a encore découvert (ou révélé) les défaillances de la sécurité d'un système ne signifie pas qu'il n'en existe pas ou qu'il ne peut pas en exister. Vous devez planifier la sécurité au cours de la phase de conception du projet, ainsi que la manière dont la sécurité sera maintenue tout au long de la durée de vie de l'application.

## <a name="design-for-security"></a>Concevoir la sécurité

 L'un des principaux problèmes liés au développement d'applications sécurisées est que la sécurité constitue souvent un aspect pris en considération après coup, après qu'un projet a été complètement codé. Le fait de ne pas concevoir la sécurité dans une application au début engendre des applications non sécurisées, car ce qui rend une application sûre n'a pas été pris en compte.

 La mise en œuvre de la sécurité de dernière minute entraîne davantage de bogues, car les logiciels s’interrompent sous les nouvelles restrictions ou doivent être réécrits pour tenir compte des fonctionnalités imprévues. Chaque ligne de code révisé ouvre la possibilité d'introduire un nouveau bogue. C’est pourquoi vous devez songer à la sécurité à un stade précoce du processus de développement, de façon à pouvoir la développer en même temps que les nouvelles fonctionnalités.

### <a name="threat-modeling"></a>Modélisation des menaces

 Vous ne pouvez pas protéger un système contre une attaque si vous ne comprenez pas toutes les attaques potentielles auxquelles il est exposé. Le processus d’évaluation des menaces de sécurité, appelé *modélisation des menaces*, est nécessaire pour déterminer la probabilité et les ramifications des failles de sécurité dans votre application ADO.net.

 La modélisation des menaces est constituée de trois étapes principales : compréhension de la perspective de l'adversaire, caractérisation de la sécurité du système et détermination des menaces.

 La modélisation des menaces représente une approche itérative pour évaluer les vulnérabilités de votre application, afin de déceler les plus dangereuses, qui exposent les données les plus sensibles. Une fois ces vulnérabilités identifiées, vous les classez par ordre de gravité et créez un ensemble de contre-mesures pour contrer les menaces selon leurs niveaux de priorité respectifs.

Pour plus d’informations, consultez les ressources suivantes :

|Ressource|Description|
|--------------|-----------------|
|Le site de [modélisation des menaces](https://www.microsoft.com/securityengineering/sdl/threatmodeling) sur le portail ingénierie de sécurité|Les ressources de cette page vous aideront à comprendre le processus de modélisation des menaces et à construire des modèles de menaces que vous pouvez utiliser pour sécuriser vos propres applications|

## <a name="the-principle-of-least-privilege"></a>Principe des privilèges minimum

 Lorsque vous concevez, générez et déployez votre application, vous devez partir du principe qu'elle va être attaquée. Souvent, ces attaques proviennent de code malveillant qui s'exécute avec les autorisations de l'utilisateur exécutant le code. D'autres peuvent provenir de code bien intentionné qui a été exploité par un pirate. Lorsque vous planifiez la sécurité, supposez toujours que le pire scénario va se produire.

 Vous pouvez employer une contre-mesure qui consiste à tenter d'ériger autant de murs autour de votre code que possible, en l'exécutant avec des privilèges minimum. Le principe des privilèges minimum consiste à accorder des droits sur un minimum de code pendant la durée de temps la plus courte nécessaire pour effectuer le travail.

 La recommandation concernant la création d’applications sécurisées consiste à démarrer sans autorisation du tout, puis d’ajouter les autorisations les plus minimales pour la tâche spécifique en cours de réalisation. En revanche, démarrer avec toutes les autorisations puis en refuser individuellement génère des applications non sécurisées, plus difficiles à tester et à maintenir en raison de l'existence éventuelle de brèches dans la sécurité causées par l'octroi involontaire d'autorisations superflues.

Pour plus d’informations sur la sécurisation de vos applications, consultez les ressources suivantes :

|Ressource|Description|
|--------------|-----------------|
|[Sécurisation des applications](/visualstudio/ide/securing-applications)|Contient des liens vers des rubriques de sécurité générales. Contient également des liens vers des rubriques pour sécuriser des applications distribuées, des applications Web, des applications mobiles et des applications de bureau.|

## <a name="code-access-security-cas"></a>Sécurité d'accès du code

La sécurité d'accès au code est un mécanisme qui aide à limiter l'accès dont dispose le code aux ressources et opérations protégées. Dans le .NET Framework, la sécurité d'accès du code remplit les fonctions suivantes :

- Définit les autorisations et les jeux d'autorisations qui représentent le droit d'accéder à diverses ressources système.

- Permet aux administrateurs de configurer la stratégie de sécurité en associant les ensembles d'autorisations à des groupes de code.

- Autorise le code à demander les autorisations nécessaires à son exécution, ainsi que les autorisations éventuellement utiles, puis spécifie les autorisations que le code ne doit jamais avoir.

- Octroie des autorisations à chaque assembly chargé, en fonction des autorisations demandées par le code et des opérations autorisées par la stratégie de sécurité.

- Permet au code de demander que ses appelants possèdent des autorisations spécifiques.

- Permet au code de demander que ses appelants possèdent une signature numérique, ce qui permet ainsi que l'appel du code protégé soit uniquement effectué par des appelants d'une organisation ou d'un site spécifique.

- Applique des restrictions sur le code au moment de l'exécution en comparant les autorisations accordées de chaque appelant sur la pile d'appels avec les autorisations que les appelants doivent posséder.

Pour réduire l'étendue des dommages pouvant se produire en cas d'attaque réussie, choisissez un contexte de sécurité pour votre code, qui accorde un accès uniquement aux ressources dont il a besoin pour effectuer son travail et à aucune autre.

Pour plus d’informations, consultez les ressources suivantes :

|Ressource|Description|
|--------------|-----------------|
|[Sécurité d'accès du code et ADO.NET](code-access-security.md)|Décrit les interactions entre la sécurité d'accès du code, la sécurité basée sur les rôles et les environnements avec un niveau de confiance partielle depuis la perspective d'une application ADO.NET.|
|[Sécurité d'accès du code](../../misc/code-access-security.md)|Contient des liens vers des rubriques supplémentaires qui décrivent la sécurité d'accès du code dans le .NET Framework.|

## <a name="database-security"></a>Sécurité de base de données

Le principe des privilèges minimum s'applique également à votre source de données. Ci-dessous figurent quelques-unes des instructions générales concernant la sécurité de la base de données :

- Créez des comptes avec les privilèges les moins élevés possible.

- N'autorisez pas les utilisateurs à accéder aux comptes d'administration uniquement pour faire fonctionner le code.

- Ne retournez pas de messages d'erreur côté serveur pour les applications clientes.

- Validez toutes les entrées sur le client et le serveur.

- Utilisez des commandes paramétrées et évitez les instructions SQL dynamiques.

- Activez l'audit de sécurité et la journalisation pour la base de données que vous utilisez, afin d'être alerté en cas de brèches de sécurité.

Pour plus d’informations, consultez les ressources suivantes :

|Ressource|Description|
|--------------|-----------------|
|[Sécurité SQL Server](./sql/sql-server-security.md)|Fournit une vue d'ensemble de la sécurité de SQL Server avec des scénarios d'application qui fournissent des conseils pour créer des applications ADO.NET sécurisées qui ciblent SQL Server.|
|[Recommandations pour les stratégies d’accès aux données](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Fournit des recommandations pour l'accès aux données et l'exécution d'opérations de base de données.|

## <a name="security-policy-and-administration"></a>Stratégie et administration de sécurité

Une administration incorrecte de la sécurité d'accès du code peut potentiellement créer des failles en matière de sécurité. Une fois qu'une application a été déployée, des techniques de surveillance de la sécurité doivent être utilisées et les risques évalués à mesure que de nouvelles menaces émergent.

Pour plus d’informations, consultez les ressources suivantes :

|Ressource|Description|
|--------------|-----------------|
|[Gestion des stratégies de sécurité](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Fournit des informations sur la création et l'administration de la stratégie de sécurité.|
|[Meilleures pratiques pour la stratégie de sécurité](/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Fournit des liens qui décrivent comment administrer la stratégie de sécurité.|

## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](securing-ado-net-applications.md)
- [Sécurité dans .NET](../../../standard/security/index.md)
- [Sécurité SQL Server](./sql/sql-server-security.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
