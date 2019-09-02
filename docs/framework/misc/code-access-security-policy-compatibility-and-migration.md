---
title: Compatibilité de la stratégie de sécurité d'accès du code et migration
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9563dae9ba5d144300549e7f33f5f5a9feb1d410
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205626"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Compatibilité de la stratégie de sécurité d'accès du code et migration

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

La partie stratégie de la sécurité d’accès du code (CAS) a été rendue obsolète dans le .NET Framework 4. Par conséquent, vous pouvez rencontrer des avertissements de compilation et des exceptions d’exécution si vous appelez les membres et les types de stratégie obsolètes [explicitement](#explicit_use) ou [implicitement](#implicit_use) (par le biais d’autres types et membres).

Vous pouvez éviter les avertissements et les erreurs comme suit :

- [Migration](#migration) vers le .NET Framework 4 remplacements pour les appels obsolètes.

   \- ou -

- Utilisation de l' [ \<élément de configuration NetFx40_LegacySecurityPolicy >](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pour choisir le comportement de stratégie CAS hérité.

Cette rubrique contient les sections suivantes :

- [Utilisation explicite](#explicit_use)

- [Utilisation implicite](#implicit_use)

- [Erreurs et avertissements](#errors_and_warnings)

- [Passage Remplacement des appels obsolètes](#migration)

- [Compatibilité Utilisation de l’option stratégie CAS héritée](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>Utilisation explicite

Les membres qui manipulent directement la stratégie de sécurité ou nécessitent la stratégie CAS en mode bac à sable (sandbox) sont obsolètes et généreront des erreurs par défaut.

En voici quelques exemples :

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a>Utilisation implicite

Plusieurs surcharges de chargement d'assembly génèrent des erreurs du fait de leur utilisation implicite de stratégie CAS. Ces surcharges prennent un paramètre <xref:System.Security.Policy.Evidence> utilisé pour résoudre la stratégie CAS et fournissent un jeu d'autorisations pour un assembly.

Voici quelques exemples. Les surcharges obsolètes sont celles qui prennent <xref:System.Security.Policy.Evidence> comme paramètre :

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a>Erreurs et avertissements

Les types et membres obsolètes produisent les messages d'erreur suivants quand ils sont utilisés. Notez que le type <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> lui-même n'est pas obsolète.

Avertissement au moment de la compilation :

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

Exceptions runtime :

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>Passage Remplacement des appels obsolètes

### <a name="determining-an-assemblys-trust-level"></a>Détermination du niveau de confiance d'un assembly

La stratégie CAS est souvent utilisée pour déterminer le jeu d'autorisations ou le niveau de confiance d'un assembly ou d'un domaine d'application. Le .NET Framework 4 expose les propriétés utiles suivantes qui n’ont pas besoin de résoudre la stratégie de sécurité:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>Utilisation de bac à sable (sandbox) pour les domaines d'application

La méthode <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> est généralement utilisée pour la mise en bac à sable (sandbox) des assemblys dans un domaine d'application. Le .NET Framework 4 expose les membres qui n’ont pas à <xref:System.Security.Policy.PolicyLevel> être utilisés à cette fin. Pour plus d'informations, voir [Procédure : exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](how-to-run-partially-trusted-code-in-a-sandbox.md).

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Détermination d'un jeu d'autorisations sécurisé ou raisonnable pour le code d'un niveau de confiance partiel

Les hôtes doivent souvent déterminer les autorisations qui sont appropriées pour l'utilisation de bacs à sable (sandbox) pour le code hébergé. Avant la .NET Framework 4, la stratégie cas fournissait une manière de le faire <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> avec la méthode. En remplacement, .NET Framework 4 fournit la <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> méthode, qui retourne un jeu d’autorisations standard sécurisé pour la preuve fournie.

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Scénarios sans bac à sable (sandbox): Surcharges pour les chargements d’assembly

La raison de l'utilisation d'une surcharge de chargement d'assembly peut être de recourir à des paramètres qui ne sont pas autrement disponibles, au lieu d'utiliser le sandbox pour l'assembly. À partir du .NET Framework 4, les surcharges de chargement d’assembly qui <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> ne nécessitent pas d’objet en tant que <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>paramètre, par exemple, permettent ce scénario.

Si vous voulez utiliser un bac à sable (sandbox) pour un assembly, utilisez la surcharge <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>.

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Compatibilité Utilisation de l’option stratégie CAS héritée

L’élément de [configuration NetFx40_LegacySecurityPolicy > vous permet de spécifier qu’un processus ou une bibliothèque utilise la stratégie CAS héritée. \<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) Quand vous activez cet élément, les surcharges de stratégie et de preuve fonctionnent comme dans les versions antérieures du Framework.

> [!NOTE]
> Le comportement de la stratégie CAS est spécifié par version du runtime ; la modification de la stratégie CAS pour une version du runtime n'affecte donc pas la stratégie CAS d'une autre version.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
