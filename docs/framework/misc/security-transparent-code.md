---
title: Code transparent de sécurité (security-transparent)
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
ms.openlocfilehash: ca251ec3084d40269b107e7bd8bef708e8d49622
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215837"
---
# <a name="security-transparent-code"></a>Code transparent de sécurité (security-transparent)

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

La sécurité fait intervenir trois éléments interactifs : le sandboxing, les autorisations et la mise en application. Le sandboxing renvoie à la pratique qui consiste à créer des domaines isolés où une partie du code est considérée comme de niveau de confiance totale et l'autre partie du code se limite au jeu d'autorisations accordées au bac à sable (sandbox). Le code d'application qui s'exécute dans le jeu d'autorisations du bac à sable est considéré comme étant transparent. Autrement dit, il ne peut effectuer aucune opération qui puisse nuire à la sécurité. Le jeu d'autorisations octroyé au bac à sable est déterminé par la preuve (classe <xref:System.Security.Policy.Evidence>). La preuve identifie les autorisations spécifiques dont ont besoin les bacs à sable et les types de bac à sable qui peuvent être créés. La mise en application consiste à autoriser le code transparent à s'exécuter uniquement dans le cadre de son jeu d'autorisations.

> [!IMPORTANT]
> La stratégie de sécurité était un élément clé dans les versions précédentes du .NET Framework. À partir du .NET Framework 4, la stratégie de sécurité est obsolète. L'élimination de la stratégie de sécurité est indépendante de la transparence de la sécurité. Pour plus d’informations sur les effets de cette modification, consultez [compatibilité et migration de la stratégie de sécurité d’accès du code](code-access-security-policy-compatibility-and-migration.md).

## <a name="purpose-of-the-transparency-model"></a>Objectif du modèle de transparence

La transparence est un mécanisme de mise en application qui fait une distinction entre le code qui s'exécute dans le cadre de l'application et le code qui s'exécute dans le cadre de l'infrastructure. La transparence établit une distinction entre le code qui peut effectuer des actions privilégiées (code critique), notamment appeler le code natif, et le code qui ne le peut pas (code transparent). Le code transparent peut exécuter des commandes dans les limites du jeu d'autorisations dont il dépend, mais ne peut pas exécuter ou contenir de code critique ni en dériver.

L'objectif principal de la mise en application de la transparence est de fournir un mécanisme simple et efficace qui permette d'isoler les différents groupes de code en fonction des privilèges. Dans le contexte du modèle de sandboxing, ces groupes de privilèges ont soit un niveau de confiance totale (c'est-à-dire, sans aucune restriction), soit un niveau de confiance partielle (c'est-à-dire, limité au jeu d'autorisations octroyé au bac à sable).

> [!IMPORTANT]
> Le modèle de transparence surpasse la sécurité d'accès du code. La transparence est mise en application par le compilateur juste-à-temps et reste en vigueur quel que soit le jeu d'autorisations octroyé à un assembly, y compris le niveau de confiance totale.

La transparence a été introduite dans le .NET Framework version 2.0 pour simplifier le modèle de sécurité et faciliter l'écriture et le déploiement de bibliothèques et d'applications sécurisées. Le code transparent est aussi utilisé dans Microsoft Silverlight pour simplifier le développement d'applications de niveau de confiance partielle.

> [!NOTE]
> Quand vous développez une application de niveau de confiance partielle, vous devez connaître les exigences d'autorisation pour vos hôtes cibles. Vous pouvez développer une application qui fasse appel à des ressources non autorisées par certains hôtes. Cette application se compilera sans erreur, mais son chargement dans l'environnement hébergé échouera. Si vous avez développé votre application l'aide de Visual Studio, vous pouvez activer le débogage en mode confiance partielle ou dans un jeu d'autorisations restreint à partir de l'environnement de développement. Pour plus d'informations, consultez [How to: Debug a ClickOnce Application with Restricted Permissions](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). La fonctionnalité de calcul des autorisations fournie pour les applications ClickOnce est aussi accessible à n'importe quelle application de niveau de confiance partielle.

## <a name="specifying-the-transparency-level"></a>Spécification du niveau de transparence

L'attribut <xref:System.Security.SecurityRulesAttribute> au niveau niveau de l'assembly sélectionne explicitement les règles <xref:System.Security.SecurityRuleSet> que suivra l'assembly. Les règles sont organisées selon un système de niveaux numériques où les niveaux supérieurs représentent une mise en application plus stricte des règles de sécurité.

Voici les différents niveaux :

- Niveau 2 (<xref:System.Security.SecurityRuleSet.Level2>) : règles de transparence .NET Framework 4.

- niveau 1 (<xref:System.Security.SecurityRuleSet.Level1>) : règles de transparence du .NET Framework 2.0.

La principale différence entre les deux niveaux de transparence est que le niveau 1 n'applique pas les règles de transparence aux appels en provenance de l'extérieur de l'assembly et vise uniquement la compatibilité.

> [!IMPORTANT]
> Vous ne devez spécifier une transparence de niveau 1 qu'à des fins de compatibilité. Autrement dit, ne spécifiez le niveau 1 que pour du code développé avec le .NET Framework version 3.5 ou antérieure qui utilise l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ou qui n'utilise pas le modèle de transparence. Par exemple, utilisez la transparence de niveau 1 pour les assemblys du .NET Framework 2.0 qui autorisent les appels des appelants ayant un niveau de confiance partielle (APTCA). Pour le code développé pour le .NET Framework 4, utilisez toujours la transparence de niveau 2.

### <a name="level-2-transparency"></a>Transparence de niveau 2

La transparence de niveau 2 a été introduite dans le .NET Framework 4. Les trois principes de ce modèle sont le code transparent, le code critique sécurisé et le code critique de sécurité.

- Le code transparent, quelles que soient les autorisations qui lui sont octroyées (y compris le niveau de confiance totale), ne peut appeler qu'un autre code transparent ou du code critique sécurisé. Si le code bénéficie d'un niveau de confiance partielle, il ne peut effectuer que les actions autorisées par le jeu d'autorisations du domaine. Voici ce que le code transparent ne peut pas faire :

  - effectuer une opération <xref:System.Security.CodeAccessPermission.Assert%2A> ou une élévation de privilèges ;

  - contenir du code non sécurisé ou non vérifiable ;

  - appeler directement du code critique ;

  - appeler du code natif ou du code possédant l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> ;

  - appeler un membre protégé par un <xref:System.Security.Permissions.SecurityAction.LinkDemand> ;

  - hériter de types critiques.

    Par ailleurs, les méthodes transparentes ne peuvent pas substituer des méthodes virtuelles critiques ni implémenter des méthodes d'interface critiques.

- Le code critique sécurisé est entièrement fiable, mais peut être appelé par du code transparent. Il expose une surface limitée de code de niveau de confiance totale. Des vérifications d'exactitude et de sécurité s'opèrent dans le code critique sécurisé.

- Le code critique de sécurité peut appeler n'importe quel code et bénéficie d'un niveau de confiance totale, mais il ne peut pas être appelé par du code transparent.

### <a name="level-1-transparency"></a>Transparence de niveau 1

Le modèle de transparence de niveau 1 a été introduit dans le .NET Framework version 2.0 pour permettre aux développeurs de réduire la quantité de code soumise à un audit de sécurité. Bien que la transparence de niveau 1 ait été mise à la disposition du public dans la version 2.0, elle a été essentiellement utilisée en interne par Microsoft à des fins d'audit de sécurité. Grâce aux annotations, les développeurs peuvent déclarer les types et les membres qui peuvent exécuter des élévations de sécurité et d'autres actions approuvées (critiques de sécurité), et ceux qui ne le peuvent pas (transparents de sécurité). Le code identifié comme étant transparent ne nécessite pas un niveau d'audit de sécurité élevé. La transparence de niveau 1 indique que la mise en application de la transparence est limitée à l'assembly. En d'autres termes, les types ou membres publics identifiés comme étant critiques de sécurité ne le sont qu'à l'intérieur de l'assembly. Si vous voulez assurer la sécurité de ces types et membres quand ils sont appelées en dehors de l'assembly, vous devez utiliser des demandes de liaison pour le niveau de confiance totale. Si vous ne le faites pas, les types et membres critiques de sécurité visibles publiquement sont traités comme étant critiques sécurisés et peuvent être appelés par du code de niveau de confiance partielle en dehors de l'assembly.

Le modèle de transparence de niveau 1 présente les limitations suivantes :

- Les types et membres critiques de sécurité publics sont accessibles à partir de code transparent de sécurité.

- Les annotations de transparence ne sont appliquées qu'au sein d'un assembly.

- Les types et membres critiques de sécurité doivent utiliser des demandes de liaison pour assurer la sécurité des appels émis en dehors de l'assembly.

- Les règles d'héritage ne sont pas appliquées.

- Le potentiel de nuisance du code transparent est bien réel quand il est exécuté en mode confiance totale.

## <a name="transparency-enforcement"></a>Mise en application de la transparence

Les règles de transparence ne sont pas appliquées tant que la transparence n'est pas calculée. Dès lors, une exception <xref:System.InvalidOperationException> est levée en cas de violation d'une règle de transparence. Le moment où la transparence est calculée dépend de plusieurs facteurs et ne peut pas être prédite. Elle est calculée le plus tard possible. Dans le .NET Framework 4, le calcul de la transparence au niveau de l’assembly se produit plus tôt que dans le .NET Framework 2,0. La seule garantie est que le calcul de la transparence se produit dès que cela est nécessaire. Cela est comparable à la façon dont le compilateur juste-à-temps (JIT) peut modifier le point au moment où une méthode est compilée et que des erreurs sont détectées dans cette méthode. Le calcul de la transparence n'est pas perceptible si votre code ne présente aucune erreur de transparence.

## <a name="see-also"></a>Voir aussi

- [Code transparent de sécurité, niveau 1](security-transparent-code-level-1.md)
- [Code transparent de sécurité, niveau 2](security-transparent-code-level-2.md)
