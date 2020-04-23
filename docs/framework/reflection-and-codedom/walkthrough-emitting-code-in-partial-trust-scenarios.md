---
title: 'Procédure pas à pas : émission de code dans des scénarios de confiance partielle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection emit, anonymously hosted dynamic methods
- partial trust, reflection
- partial trust, emitting dynamic methods
- reflection emit, partial trust scenarios
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
ms.openlocfilehash: fd420c9754494b95c55df403edec87743572db03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129991"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>Procédure pas à pas : émission de code dans des scénarios de confiance partielle

L’émission de réflexion utilise le même ensemble d’API en confiance totale ou partielle, mais certaines fonctionnalités nécessitent des autorisations spéciales dans le code avec confiance partielle. En outre, l’émission de réflexion a une fonctionnalité, des méthodes dynamiques hébergées anonymement, qui est conçue pour être utilisée avec une confiance partielle et par les assemblys transparents de sécurité.

> [!NOTE]
> Avant .NET Framework 3.5, l’émission de code nécessitait <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType>. Par défaut, cette autorisation est comprise dans les jeux d’autorisations nommés `FullTrust` et `Intranet`, mais pas dans le jeu d’autorisations `Internet`. Par conséquent, une bibliothèque pourrait être utilisée avec une confiance partielle seulement si elle avait l’attribut <xref:System.Security.SecurityCriticalAttribute> et exécutait aussi une méthode <xref:System.Security.PermissionSet.Assert%2A> pour <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Ces bibliothèques nécessitent une revue minutieuse de la sécurité, car les erreurs de codage peuvent entraîner des failles de sécurité. .NET Framework 3.5 permet au code d’être émis dans des scénarios de confiance partielle sans émettre de demandes de sécurité, car la génération de code n’est pas fondamentalement une opération nécessitant des privilèges. Autrement dit, le code généré n'a pas plus d'autorisations que l'assembly qui l'émet. Ainsi, les bibliothèques qui émettent du code sont transparentes de sécurité et il devient inutile de déclarer <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit> puisque l’écriture d’une bibliothèque sécurisée ne nécessite pas une révision aussi approfondie de la sécurité.

Cette procédure pas à pas décrit les tâches suivantes :

- [Configuration d’un bac à sable (sandbox) simple pour le test de code partiellement fiable](#Setting_up).

  > [!IMPORTANT]
  > Il s’agit d’un moyen simple de faire des essais avec du code partiellement fiable. Pour exécuter du code qui provient d’emplacements non approuvés, consultez [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md).

- [Exécution de code dans des domaines d’application partiellement fiables](#Running_code).

- [Utilisation de méthodes dynamiques hébergées anonymement pour émettre et exécuter du code en confiance partielle](#Using_methods).

Pour plus d’informations sur l’émission de code dans des scénarios de confiance partielle, consultez [Problèmes de sécurité dans l’émission de réflexion](security-issues-in-reflection-emit.md).

Pour obtenir une liste complète du code utilisé dans ces procédures, consultez la [section Exemple](#Example) à la fin de cette procédure pas à pas.

<a name="Setting_up"></a>

## <a name="setting-up-partially-trusted-locations"></a>Configuration des emplacements partiellement fiables

Les deux procédures suivantes montrent comment configurer des emplacements à partir desquels vous pouvez tester du code avec une confiance partielle.

- La première procédure montre comment créer un domaine d’application sandbox dans lequel le code a des autorisations Internet.

- La seconde procédure montre comment ajouter <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> à un domaine d’application partiellement fiable pour activer l’accès aux données privées dans des assemblys d’une confiance inférieure ou égale.

### <a name="creating-sandboxed-application-domains"></a>Création de domaines d’application sandbox

Pour créer un domaine d’application dans lequel vos assemblys s’exécutent avec une confiance partielle, vous devez spécifier le jeu d’autorisations à accorder aux assemblys en utilisant la surcharge de la méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> pour créer le domaine d’application. Pour spécifier le jeu d’autorisations, le plus simple est de récupérer un jeu d’autorisations nommé auprès de la stratégie de sécurité.

La procédure suivante crée un domaine d’application sandbox qui exécute votre code avec une confiance partielle pour tester des scénarios dans lesquels le code émis peut accéder seulement à des membres publics de types public. La procédure qui vient après montre comment ajouter <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> pour tester des scénarios dans lesquels le code émis peut accéder aux types et aux membres non publics dans les assemblys bénéficiant d’autorisations inférieures ou égales.

#### <a name="to-create-an-application-domain-with-partial-trust"></a>Pour créer un domaine d’application avec une confiance partielle

1. Créez un jeu d’autorisations à accorder aux assemblys dans le domaine d’application sandbox. Dans ce cas, le jeu d’autorisations de la zone Internet est utilisé.

    [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
    [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]

2. Créez un objet <xref:System.AppDomainSetup> pour initialiser le domaine d’application avec un chemin d’application.

    > [!IMPORTANT]
    > Pour simplifier, cet exemple de code utilise le dossier actif. Pour exécuter du code qui provient d’Internet, utilisez un dossier distinct pour le code non fiable, comme décrit dans [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md).

    [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
    [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]

3. Créez le domaine d’application en spécifiant les informations de configuration du domaine d’application et le jeu d’autorisations accordé pour tous les assemblys qui s’exécutent dans le domaine d’application.

    [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
    [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]

    Le dernier paramètre de la surcharge de la méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> vous permet de spécifier un ensemble d’assemblys auxquels une confiance totale est accordée, à la place du jeu d’autorisations du domaine d’application. Il n’est pas nécessaire de spécifier les assemblys .NET Framework utilisés par votre application, car ces assemblys se trouvent dans le Global Assembly Cache. Les assemblys présents dans le Global Assembly Cache sont toujours totalement fiables. Vous pouvez utiliser ce paramètre pour spécifier des assemblys avec nom fort qui ne sont pas dans le Global Assembly Cache.

### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Ajout de RestrictedMemberAccess à des domaines sandbox

Les applications hôtes peuvent autoriser les méthodes dynamiques hébergées anonymement à accéder aux données privées dans les assemblys qui ont des niveaux de confiance inférieurs ou égaux au niveau de confiance de l’assembly qui émet le code. Pour permettre cette possibilité limitée d’ignorer les contrôles de visibilité juste-à-temps (JIT), l’application hôte ajoute un objet <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> (RMA) au jeu d’autorisations.

Par exemple, un hôte peut accorder des autorisations Internet plus RMA à des applications Internet, pour qu’une application Internet puisse émettre du code qui accède aux données privées dans ses propres assemblys. Étant donné que l’accès est limité aux assemblys de confiance inférieure ou égale, une application Internet ne peut pas accéder aux membres des assemblys entièrement fiables, comme les assemblys .NET Framework.

> [!NOTE]
> Pour empêcher une élévation de privilèges, les informations de pile de l’assembly émetteur sont incluses lors de la construction des méthodes dynamiques hébergées anonymement. Quand la méthode est appelée, les informations de pile sont vérifiées. Par conséquent, une méthode dynamique hébergée anonymement qui est appelée à partir d’un code totalement fiable est toujours limitée au niveau de confiance de l’assembly émetteur.

#### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Pour créer un domaine d’application avec une confiance partielle plus RMA

1. Créez un objet <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (RMA) et utilisez la méthode <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> pour ajouter l’autorisation au jeu d’autorisations.

    [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
    [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]

    La méthode <xref:System.Security.PermissionSet.AddPermission%2A> ajoute l’autorisation au jeu d’autorisations si elle n’y est pas déjà. Si l’autorisation est déjà dans le jeu d’autorisations, les indicateurs spécifiés sont ajoutés à l’autorisation existante.

    > [!NOTE]
    > RMA est une fonctionnalité des méthodes dynamiques hébergées anonymement. Quand des méthodes dynamiques ordinaires ignorent les contrôles de visibilité JIT, le code émis nécessite une confiance totale.

2. Créez le domaine d’application en spécifiant les informations de configuration du domaine d’application et le jeu d’autorisations.

    [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
    [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]

<a name="Running_code"></a>

## <a name="running-code-in-sandboxed-application-domains"></a>Exécution de code dans des domaines d’application sandbox

La procédure suivante explique comment définir une classe en utilisant des méthodes qui peuvent être exécutées dans un domaine d’application, comment créer une instance de la classe dans le domaine et comment exécuter ses méthodes.

#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Pour définir et exécuter une méthode dans un domaine d’application

1. Définissez une classe qui dérive de <xref:System.MarshalByRefObject>. Cette opération vous permet de créer des instances de la classe dans d’autres domaines d’application et d’effectuer des appels de méthode à travers les limites du domaine d’application. Dans cet exemple, la classe est nommée `Worker`.

    [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
    [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]

2. Définissez une méthode publique qui contient le code que vous voulez exécuter. Dans cet exemple, le code émet une méthode dynamique simple, crée un délégué pour exécuter la méthode et appelle le délégué.

    [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
    [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]

3. Dans votre programme principal, obtenez le nom d’affichage de votre assembly. Ce nom est utilisé quand vous créez des instances de la classe `Worker` dans le domaine d’application sandbox.

    [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
    [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]

4. Dans votre programme principal, créez un domaine d’application sandbox, comme décrit dans [la première procédure](#Setting_up) de cet article. Vous ne devez pas ajouter des autorisations au jeu d’autorisations `Internet`, car la méthode `SimpleEmitDemo` utilise uniquement des méthodes publiques.

5. Dans votre programme principal, créez une instance de la classe `Worker` dans le domaine d’application sandbox.

    [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
    [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]

    La méthode <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> crée l’objet dans le domaine d’application cible et retourne un proxy qui peut être utilisé pour appeler les propriétés et les méthodes de l’objet.

    > [!NOTE]
    > Si vous utilisez ce code dans Visual Studio, vous devez changer le nom de la classe pour y inclure l’espace de noms. Par défaut, l’espace de noms est le nom du projet. Par exemple, si le projet est « PartialTrust », le nom de la classe doit être « PartialTrust.Worker ».

6. Ajoutez le code pour appeler la méthode `SimpleEmitDemo`. L’appel est marshalé à travers la limite du domaine d’application et le code est exécuté dans le domaine d’application sandbox.

    [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
    [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]

<a name="Using_methods"></a>

## <a name="using-anonymously-hosted-dynamic-methods"></a>Utilisation de méthodes dynamiques hébergées anonymement

Les méthodes dynamiques hébergées anonymement sont associées à un assembly transparent fourni par le système. Par conséquent, le code qu’elles contiennent est transparent. Les méthodes dynamiques ordinaires doivent quant à elles être associées à un module existant (qu’il soit spécifié directement ou inféré depuis un type associé) et prendre leur niveau de sécurité de ce module.

> [!NOTE]
> La seule façon d’associer une méthode dynamique à l’assembly qui fournit l’hébergement anonyme est d’utiliser les constructeurs qui sont décrits dans la procédure suivante. Vous ne pouvez pas spécifier explicitement un module dans l’assembly hébergeur anonyme.

Les méthodes dynamiques ordinaires ont accès aux membres internes du module auquel elles sont associées ou aux membres privés du type auquel elles sont associées. Comme les méthodes dynamiques hébergées anonymement sont isolées du reste du code, elles n’ont pas accès aux données privées. Toutefois, elles ont une possibilité limitée d’ignorer les contrôles de visibilité JIT pour accéder aux données privées. Cette possibilité est limitée aux assemblys qui ont des niveaux de confiance inférieurs ou égaux au niveau de confiance de l’assembly qui émet le code.

Pour empêcher une élévation de privilèges, les informations de pile de l’assembly émetteur sont incluses lors de la construction des méthodes dynamiques hébergées anonymement. Quand la méthode est appelée, les informations de pile sont vérifiées. Une méthode dynamique hébergée anonymement qui est appelée à partir d’un code totalement fiable est toujours limitée au niveau de confiance de l’assembly émetteur.

#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Pour utiliser des méthodes dynamiques hébergées anonymement

- Créez une méthode dynamique hébergée anonymement en utilisant un constructeur qui ne spécifie pas un module ou un type associé.

  [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
  [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]

  Si une méthode dynamique hébergée anonymement utilise seulement des méthodes et des types publics, elle ne nécessite pas un accès restreint aux membres et n’a pas à ignorer les contrôles de visibilité JIT.

  Aucune autorisation spéciale n’est nécessaire pour émettre une méthode dynamique, mais le code émis nécessite les autorisations demandées par les types et les méthodes qu’il utilise. Par exemple, si le code émis appelle une méthode qui accède à un fichier, il nécessite <xref:System.Security.Permissions.FileIOPermission>. Si le niveau de confiance n’inclut pas cette autorisation, une exception de sécurité est levée quand le code émis est exécuté. Le code montré ici émet une méthode dynamique qui utilise seulement la méthode <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>. Par conséquent, le code peut être exécuté à partir d’emplacements partiellement fiables.

- Vous pouvez aussi créer une méthode dynamique hébergée anonymement avec une possibilité limitée d’ignorer les contrôles de visibilité JIT, en utilisant le constructeur <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> et en spécifiant `true` pour le paramètre `restrictedSkipVisibility`.

  [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
  [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]

  La restriction est que la méthode dynamique hébergée anonymement peut accéder aux données privées seulement dans les assemblys avec des niveaux de confiance inférieurs ou égaux à celui de l’assembly émetteur. Par exemple, si la méthode dynamique s’exécute avec une confiance Internet, elle peut accéder aux données privées d’autres assemblys qui s’exécutent aussi avec la confiance Internet, mais elle ne peut pas accéder aux données privées des assemblys .NET Framework. Les assemblys .NET Framework sont installés dans le Global Assembly Cache et sont toujours entièrement fiables.

  Les méthodes dynamiques hébergées anonymement peuvent utiliser cette possibilité limitée d’ignorer les contrôles de visibilité JIT seulement si l’application hôte accorde <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>. La demande de cette autorisation est effectuée quand la méthode est appelée.

  > [!NOTE]
  > Les informations de la pile des appels de l’assembly émetteur sont incluses lors de la construction de la méthode dynamique. Par conséquent, la demande porte sur les autorisations de l’assembly émetteur au lieu de l’assembly qui appelle la méthode. Ceci empêche l’exécution du code émis avec des autorisations élevées.

  L’[exemple de code complet](#Example) à la fin de cette procédure pas à pas montre l’utilisation et les limitations de l’accès restreint aux membres. Sa classe `Worker` comprend une méthode qui peut créer des méthodes dynamiques hébergées anonymement avec ou sans la possibilité limitée d’ignorer les contrôles de visibilité. L’exemple montre le résultat de l’exécution de cette méthode dans des domaines d’application qui ont des niveaux de confiance différents.

  > [!NOTE]
  > La possibilité limitée d’ignorer les contrôles de visibilité est une fonctionnalité des méthodes dynamiques hébergées anonymement. Quand des méthodes dynamiques ordinaires ignorent les contrôles de visibilité JIT, une confiance totale leur est accordée.

<a name="Example"></a>

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple de code suivant montre l’utilisation de l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> pour permettre aux méthodes dynamiques hébergées anonymement d’ignorer les contrôles de visibilité JIT, mais seulement quand le membre cible est à un niveau de confiance inférieur ou égal à celui de l’assembly qui émet le code.

L’exemple définit une classe `Worker` qui peut être marshalée à travers les limites du domaine d’application. La classe a deux surcharges de la méthode `AccessPrivateMethod`, qui émettent et exécutent des méthodes dynamiques. La première surcharge émet une méthode dynamique qui appelle la méthode `PrivateMethod` privée de la classe `Worker`, et peut émettre la méthode dynamique avec ou sans contrôles de visibilité JIT. La deuxième surcharge émet une méthode dynamique qui accède à une propriété `internal` (la propriété `Friend` en Visual Basic) de la classe <xref:System.String>.

L’exemple utilise une méthode d’assistance pour créer un jeu d’autorisations limité aux autorisations `Internet`, puis crée un domaine d’application en utilisant la surcharge de la méthode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> pour spécifier que tout le code qui s’exécute dans le domaine utilise ce jeu d’autorisations. L’exemple crée une instance de la classe `Worker` dans le domaine d’application et exécute deux fois la méthode `AccessPrivateMethod`.

- La première fois que la méthode `AccessPrivateMethod` est exécutée, les contrôles de visibilité JIT sont appliqués. La méthode dynamique échoue quand elle est appelée, car les contrôles de visibilité JIT l’empêchent d’accéder à la méthode privée.

- La seconde fois que la méthode `AccessPrivateMethod` est exécutée, les contrôles de visibilité JIT sont ignorés. La méthode dynamique échoue lors de la compilation, car le jeu d’autorisations `Internet` n’accorde pas d’autorisations suffisantes pour ignorer les contrôles de visibilité.

L’exemple ajoute <xref:System.Security.Permissions.ReflectionPermission> avec <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> au jeu d’autorisations. L’exemple crée ensuite un second domaine en spécifiant que tout le code qui s’exécute dans le domaine reçoit les autorisations du jeu d’autorisations. L’exemple crée une instance de la classe `Worker` dans le nouveau domaine d’application et exécute les deux surcharges de la méthode `AccessPrivateMethod`.

- La première surcharge de la méthode `AccessPrivateMethod` est exécutée et les contrôles de visibilité JIT sont ignorés. La méthode dynamique se compile et s’exécute correctement, car l’assembly qui émet le code est le même que l’assembly qui contient la méthode privée. Par conséquent, les niveaux de confiance sont égaux. Si l’application qui contient la classe `Worker` avait plusieurs assemblys, le même processus réussirait pour chacun de ces assemblys, car ils seraient tous au même niveau de confiance.

- La seconde surcharge de la méthode `AccessPrivateMethod` est exécutée et les contrôles de visibilité JIT sont à nouveau ignorés. Cette fois, la méthode dynamique échoue lorsqu’elle est compilée, car elle tente d' `internal` `FirstChar` accéder à la <xref:System.String> propriété de la classe. L’assembly qui contient la classe <xref:System.String> est totalement fiable. Par conséquent, il est à un niveau de confiance plus élevé que l’assembly qui émet le code.

Cette comparaison montre comment <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> permet à du code partiellement fiable d’ignorer les contrôles de visibilité pour un autre code partiellement fiable sans compromettre la sécurité du code de confiance.

### <a name="code"></a>Code

[!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
[!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]

## <a name="compiling-the-code"></a>Compilation du code

- Si vous générez cet exemple de code dans Visual Studio, vous devez changer le nom de la classe pour inclure l’espace de noms quand vous le passez à la méthode <xref:System.AppDomain.CreateInstanceAndUnwrap%2A>. Par défaut, l’espace de noms est le nom du projet. Par exemple, si le projet est « PartialTrust », le nom de la classe doit être « PartialTrust.Worker ».

## <a name="see-also"></a>Voir aussi

- [Problèmes de sécurité dans l’émission de réflexion](security-issues-in-reflection-emit.md)
- [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
