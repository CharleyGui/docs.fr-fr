---
title: Problèmes de sécurité dans l'émission de réflexion
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- emitting dynamic assemblies, security
- reflection emit, security
- reflection emit, partial trust scenarios
- partial trust,emitting dynamic methods
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- dynamic assemblies, security
ms.assetid: 0f8bf8fa-b993-478f-87ab-1a1a7976d298
ms.openlocfilehash: d1b6994f7ee9efa9f6472deffb2f3d869606e182
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644199"
---
# <a name="security-issues-in-reflection-emit"></a>Problèmes de sécurité dans l'émission de réflexion
Le .NET Framework offre trois façons d’émettre du code MSIL (Microsoft Intermediate Language), chacune avec ses propres problèmes de sécurité :  
  
- [Assemblys dynamiques](#Dynamic_Assemblies)  
  
- [Méthodes dynamiques hébergées anonymement](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Méthodes dynamiques associées à des assemblys existants](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Quelle que soit la façon dont vous générez le code dynamique, l'exécution du code généré nécessite toutes les autorisations requises par les types et par les méthodes utilisées par le code généré.  
  
> [!NOTE]
> Les autorisations nécessaires pour la réflexion sur le code et pour l’émission de code ont changé avec les versions successives du .NET Framework. Consultez [Informations sur la version](#Version_Information) plus loin dans cette rubrique.  
  
<a name="Dynamic_Assemblies"></a>
## <a name="dynamic-assemblies"></a>Assemblys dynamiques  
 Les assemblys dynamiques sont créés à l'aide de surcharges de la méthode <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>. La plupart des surcharges de cette méthode sont dépréciées dans .NET Framework 4, en raison de la suppression de la stratégie de sécurité à l’échelle de l’ordinateur. (Voir [modifications de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).) Les surcharges restantes peuvent être exécutées par n’importe quel code, quel que soit le niveau de confiance. Ces surcharges sont réparties en deux groupes : celles qui spécifient une liste d'attributs à appliquer à l'assembly dynamique lors de sa création, et celles qui ne les spécifient pas. Si vous ne spécifiez pas le modèle de transparence pour l’assembly, en appliquant l’attribut <xref:System.Security.SecurityRulesAttribute> au moment de sa création, le modèle de transparence est hérité de l’assembly émetteur.  
  
> [!NOTE]
> Les attributs que vous appliquez à l'assembly dynamique après sa création, en utilisant la méthode <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A>, ne prennent pas effet tant que l'assembly n'a pas été enregistré sur le disque et rechargé en mémoire.  
  
 Le code d'un assembly dynamique peut accéder aux types et aux membres visibles d'autres assemblys.  
  
> [!NOTE]
> Les assemblys dynamiques n'utilisent pas les indicateurs <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> et <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, qui permettent aux méthodes dynamiques d'accéder aux types et aux membres non publics.  
  
 Les assemblys dynamiques transitoires sont créés en mémoire et ne sont jamais enregistrés sur disque : ils ne nécessitent donc pas d'autorisations d'accès à des fichiers. L'enregistrement d'un assembly dynamique sur disque requiert <xref:System.Security.Permissions.FileIOPermission> avec les indicateurs appropriés.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Génération d'assemblys dynamiques à partir de code d'un niveau de confiance partiel  
 Considérez les conditions dans lesquelles un assembly disposant d'autorisations Internet peut générer un assembly dynamique transitoire et exécuter son code :  
  
- L'assembly dynamique utilise seulement des types et des membres publics d'autres assemblys.  
  
- Les autorisations demandées par ces types et ces membres sont incluses dans le jeu d'autorisations de l'assembly partiellement approuvé.  
  
- L'assembly n'est pas enregistré sur disque.  
  
- Les symboles de débogage ne sont pas générés. (Les jeux d'autorisations `Internet` et `LocalIntranet` n'incluent pas les autorisations nécessaires.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>
## <a name="anonymously-hosted-dynamic-methods"></a>Méthodes dynamiques hébergées anonymement  
 Les méthodes dynamiques hébergées anonymement sont créées à l'aide des deux constructeurs de <xref:System.Reflection.Emit.DynamicMethod> qui ne spécifient pas un type ou un module associé, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> et <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Ces constructeurs placent les méthodes dynamiques dans un assembly fourni par le système, entièrement fiable et transparent quant à la sécurité. Aucune autorisation n'est requise pour utiliser ces constructeurs ou pour émettre du code pour les méthodes dynamiques.  
  
 Au lieu de cela, quand une méthode dynamique hébergée anonymement est créée, la pile des appels est capturée. Quand la méthode est construite, les demandes en matière de sécurité sont effectuées sur la pile des appels capturée.  
  
> [!NOTE]
> Conceptuellement, les demandes sont effectuées pendant la construction de la méthode. Autrement dit, les demandes peuvent être faites à l'émission de chaque instruction MSIL. Dans l'implémentation actuelle, toutes les demandes sont faites quand la méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> est appelée ou quand le compilateur juste-à-temps (JIT) est appelé, si la méthode est appelée sans appel de <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Si le domaine d'application le permet, les méthodes dynamiques hébergées anonymement peuvent ignorer les contrôles de visibilité JIT, avec la restriction suivante : les types et les membres non publics auxquels accède une méthode dynamique hébergée anonymement doivent être dans des assemblys dont les jeux d'autorisations doivent être équivalents à ou être des sous-ensembles du jeu d'autorisations de la pile des appels émettrice. Cette possibilité restreinte d'ignorer les contrôles de visibilité JIT est activée si le domaine d'application accorde l'autorisation <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
- Si votre méthode utilise seulement des types et des membres publics, aucune autorisation n'est requise pendant la construction.  
  
- Si vous spécifiez que les contrôles de visibilité JIT doivent être ignorés, la demande qui est faite quand la méthode est construite inclut <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> et le jeu d'autorisations de l'assembly qui contient le membre non public qui fait l'objet de l'accès.  
  
 Étant donné que le jeu d'autorisations du membre non public est pris en considération, le code d'un niveau de confiance partiel auquel l'autorisation <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a été accordée ne peut pas élever ses privilèges en exécutant des membres non publics d'assemblys approuvés.  
  
 Comme avec tout autre code émis, l'exécution de la méthode dynamique nécessite toutes les autorisations demandées par les méthodes utilisées par la méthode dynamique.  
  
 L’assembly système qui héberge des méthodes dynamiques hébergées anonymement utilise le modèle de transparence <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType>, qui est le modèle de transparence utilisé dans le .NET Framework avant .NET Framework 4.  
  
 Pour plus d'informations, consultez la classe <xref:System.Reflection.Emit.DynamicMethod>.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Génération de méthodes dynamiques hébergées anonymement à partir de code d'un niveau de confiance partiel  
 Considérez les conditions dans lesquelles un assembly disposant d'autorisations Internet peut générer une méthode dynamique hébergée anonymement et l'exécuter :  
  
- La méthode dynamique utilise seulement des types et des membres publics. Si son jeu d'autorisations inclut <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, elle peut utiliser des types et des membres non publics de tout assembly dont le jeu d'autorisations est équivalent à ou est un sous-ensemble du jeu d'autorisations de l'assembly émetteur.  
  
- Les autorisations requises par tous les types et les membres utilisés par la méthode dynamique sont incluses dans le jeu d'autorisations de l'assembly partiellement approuvé.  
  
> [!NOTE]
> Les méthodes dynamiques ne prennent pas en charge les symboles de débogage.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Méthodes dynamiques associées à des assemblys existants  
 Pour associer une méthode dynamique à un type ou un module d'un assembly existant, utilisez les constructeurs de <xref:System.Reflection.Emit.DynamicMethod> qui spécifient le type ou le module associé. Les autorisations requises pour appeler ces constructeurs varient, car l'association d'une méthode dynamique à un type ou un module existant donne à la méthode dynamique l'accès aux types et aux membres non publics :  
  
- Une méthode dynamique qui est associée à un type a accès à tous les membres de ce type, même aux membres privés, et à tous les types et les membres internes de l'assembly qui contient le type associé.  
  
- Une méthode dynamique qui est associée à un module a accès à tous les types et les membres `internal` (`Friend` en Visual Basic, `assembly` dans les métadonnées du common language runtime) du module.  
  
 En outre, vous pouvez utiliser un constructeur qui spécifie la possibilité d'ignorer les contrôles de visibilité du compilateur JIT. Procéder ainsi donne à votre méthode dynamique l'accès à tous les types et membres de tous les assemblys, quel que soit le niveau d'accès.  
  
 Les autorisations demandées par le constructeur dépendent du niveau d'accès que vous décidez de donner à votre méthode dynamique :  
  
- Si votre méthode utilise seulement des types et des membres publics, et que vous l'associez à votre propre type ou à votre propre module, aucune autorisation n'est requise.  
  
- Si vous spécifiez que les contrôles de visibilité JIT doivent être ignorés, le constructeur demande <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>.  
  
- Si vous associez la méthode dynamique à un autre type, même un autre type de votre propre assembly, le constructeur demande <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> et <xref:System.Security.Permissions.SecurityPermission> avec l'indicateur <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType>.  
  
- Si vous associez la méthode dynamique à un type ou un module d'un autre assembly, le constructeur demande deux éléments : <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> et le jeu d'autorisations de l'assembly qui contient l'autre module. Autrement dit, votre pile des appels doit inclure toutes les autorisations du jeu d'autorisations du module cible, plus <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    > Pour la compatibilité descendante, si la demande pour le jeu d'autorisations cible plus <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> échoue, le constructeur demande <xref:System.Security.Permissions.SecurityPermission> avec l'indicateur <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType>.  
  
 Bien que les éléments de cette liste soient décrits en les termes du jeu d'autorisations de l'assembly émetteur, n'oubliez pas que les demandes sont faites sur la pile des appels complète, y compris la limite du domaine de l'application.  
  
 Pour plus d'informations, consultez la classe <xref:System.Reflection.Emit.DynamicMethod>.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Génération de méthodes dynamiques à partir de code d'un niveau de confiance partiel  
  
> [!NOTE]
> La méthode recommandée pour générer des méthodes dynamiques à partir de code d’un niveau de confiance partiel consiste à utiliser des [méthodes dynamiques hébergées anonymement](#Anonymously_Hosted_Dynamic_Methods).  
  
 Considérez les conditions dans lesquelles un assembly disposant d'autorisations Internet peut générer une méthode dynamique et l'exécuter :  
  
- La méthode dynamique est associée au module ou au type qui l'émet, ou bien son jeu d'autorisations inclut <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> et elle est associée à un module d'un assembly dont le jeu d'autorisations est équivalent à ou est un sous-ensemble du jeu d'autorisations de l'assembly émetteur.  
  
- La méthode dynamique utilise seulement des types et des membres publics. Si son jeu d'autorisations inclut <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> et qu'elle est associée à un module d'un assembly dont le jeu d'autorisations est équivalent à ou est un sous-ensemble du jeu d'autorisations de l'assembly émetteur, elle peut utiliser les types et les membres marqués comme étant `internal` (`Friend` en Visual Basic, `assembly` dans les métadonnées du common language runtime) dans le module associé.  
  
- Les autorisations demandées par tous les types et les membres utilisés par la méthode dynamique sont incluses dans le jeu d'autorisations de l'assembly partiellement approuvé.  
  
- La méthode dynamique n'ignore pas les contrôles de visibilité JIT.  
  
> [!NOTE]
> Les méthodes dynamiques ne prennent pas en charge les symboles de débogage.  
  
<a name="Version_Information"></a>
## <a name="version-information"></a>Informations sur la version  
 À compter de .NET Framework 4, la stratégie de sécurité à l’échelle de l’ordinateur est supprimée et la transparence de sécurité devient le mécanisme d’application par défaut. Consultez [Changements en matière de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 À compter de .NET Framework 2.0 Service Pack 1, <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> n’est plus nécessaire lors de l’émission d’assemblys et de méthodes dynamiques. Cet indicateur est nécessaire dans toutes les versions antérieures du .NET Framework.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> est inclus par défaut dans les jeux d'autorisations nommés `FullTrust` et `LocalIntranet`, mais pas dans le jeu d'autorisations `Internet`. Par conséquent, dans les versions antérieures du .NET Framework, une bibliothèque peut être utilisée avec des autorisations Internet uniquement si elle exécute une méthode <xref:System.Security.PermissionSet.Assert%2A> pour <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Ces bibliothèques nécessitent une revue minutieuse de la sécurité, car les erreurs de codage peuvent entraîner des failles de sécurité. .NET Framework 2.0 SP1 permet au code d’être émis dans des scénarios de confiance partielle sans émettre de demandes de sécurité, car la génération de code n’est pas fondamentalement une opération nécessitant des privilèges. Autrement dit, le code généré n'a pas plus d'autorisations que l'assembly qui l'émet. Ceci permet aux bibliothèques qui émettent du code d'être transparentes de sécurité et supprime la nécessité de déclarer <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, ce qui simplifie l'écriture d'une bibliothèque sécurisée.  
  
 En outre, .NET Framework 2.0 SP1 introduit l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> pour accéder aux types et aux membres non publics à partir de méthodes dynamiques partiellement approuvées. Les versions antérieures du .NET Framework exigent l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> pour les méthodes dynamiques qui accèdent à des types et des membres non publics. Il s’agit d’une autorisation qui ne doit jamais être accordée à du code partiellement fiable.  
  
 Pour finir, .NET Framework 2.0 SP1 introduit des méthodes hébergées anonymement.  
  
### <a name="obtaining-information-on-types-and-members"></a>Obtention d'informations sur les types et les membres  
 Depuis .NET Framework 2.0, aucune autorisation n’est nécessaire pour obtenir des informations sur les types et les membres non publics. La réflexion est utilisée pour obtenir les informations nécessaires à l'émission de méthodes dynamiques. Par exemple, les objets <xref:System.Reflection.MethodInfo> sont utilisés pour émettre des appels de méthode. Les versions antérieures du .NET Framework exigent <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType>. Pour plus d’informations, consultez [Considérations relatives à la sécurité de la réflexion](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Voir aussi

- [Considérations sur la sécurité de la réflexion](security-considerations-for-reflection.md)
- [Émission d’assemblys et de méthodes dynamiques](emitting-dynamic-methods-and-assemblies.md)
