---
title: Considérations sur la sécurité de la réflexion
description: En savoir plus sur les considérations de sécurité pour la réflexion dans .NET. L’obtention d’informations sur les types et les membres est autorisée, mais l’accès aux membres a des restrictions.
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
ms.openlocfilehash: 9ef2ac4897b3f8c48a0b0f402ab06eb073a5c1fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556334"
---
# <a name="security-considerations-for-reflection"></a>Considérations sur la sécurité de la réflexion

La réflexion permet d'obtenir des informations sur les types et les membres, et d'accéder aux membres (c'est-à-dire appeler des méthodes et des constructeurs, obtenir et définir des valeurs de propriétés, ajouter et supprimer des gestionnaires d'événements, etc.). L'utilisation de la réflexion pour obtenir des informations sur les types et les membres n'est pas limitée. Tout code peut utiliser la réflexion pour effectuer les tâches suivantes :

- Énumérer les types et les membres, et examiner leurs métadonnées.

- Énumérer et examiner les assemblys et les modules.

En revanche, l'utilisation de la réflexion pour accéder aux membres est soumise à des restrictions. À compter de .NET Framework 4, seul le code de confiance peut utiliser la réflexion pour accéder aux membres critiques de sécurité. En outre, seul le code de confiance peut utiliser la réflexion pour accéder aux membres non publics qui ne seraient pas directement accessibles au code compilé. Enfin, le code qui utilise la réflexion pour accéder à un membre critique sécurisé doit avoir les autorisations demandées par ce membre, tout comme avec le code compilé.

Moyennant les autorisations nécessaires, le code peut utiliser la réflexion pour effectuer les types d'accès suivants :

- Accès aux membres publics qui ne sont pas critiques de sécurité.

- Accès aux membres non publics qui seraient accessibles au code compilé, si ces membres ne sont pas critiques de sécurité. Voici des exemples de ces membres non publics :

  - Membres protégés des classes de base du code appelant. (Dans la réflexion, ceci s'appelle l'accès au niveau de la famille.)

  - Membres `internal` (les membres `Friend` en Visual Basic) de l'assembly du code appelant. (Dans la réflexion, ceci s'appelle l'accès au niveau de l'assembly.)

  - Membres privés d'autres instances de la classe qui contient le code appelant.

Par exemple, le code qui est exécuté dans un domaine d'application sandbox est limité aux accès décrits dans cette liste, sauf si le domaine d'application accorde des autorisations supplémentaires.

À compter de .NET Framework 2.0 Service Pack 1, le fait de tenter d’accéder à des membres normalement inaccessibles génère une demande du jeu d’autorisations de l’objet cible, plus <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>. Un code qui s’exécute avec un niveau de confiance total (par exemple, le code d’une application lancée à partir de la ligne de commande) peut toujours satisfaire à ces autorisations. (Ceci est soumis aux limitations de l'accès aux membres critiques de sécurité, comme décrit plus loin dans cet article.)

De façon facultative, un domaine d’application sandbox peut accorder <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>, comme décrit dans la section [Accès aux membres normalement inaccessibles](#accessingNormallyInaccessible) plus loin dans cet article.

<a name="accessingSecurityCritical"></a>

## <a name="accessing-security-critical-members"></a>Accès aux membres critiques de sécurité

Un membre est critique du point de vue de la sécurité s'il a l'attribut <xref:System.Security.SecurityCriticalAttribute>, s'il appartient à un type qui a l'attribut <xref:System.Security.SecurityCriticalAttribute> ou s'il est dans un assembly critique du point de vue de la sécurité. À compter de .NET Framework 4, les règles d’accès aux membres critiques de sécurité sont les suivantes :

- Le code transparent ne peut pas utiliser la réflexion pour accéder aux membres critiques de sécurité, même si le code est d'un niveau de confiance total. Une exception <xref:System.MethodAccessException>, <xref:System.FieldAccessException> ou <xref:System.TypeAccessException> est levée.

- Le code qui s'exécute avec un niveau de confiance partiel est traité comme étant transparent.

Ces règles sont les mêmes si l'accès à un membre critique du point de vue de la sécurité se fait directement par du code compilé ou en utilisant la réflexion.

Le code d'application qui est exécuté à partir de la ligne de commande s'exécute avec une confiance totale. Tant qu'il n'est pas marqué comme transparent, il peut utiliser la réflexion pour accéder aux membres critiques de sécurité. Quand le même code est exécuté avec un niveau de confiance partiel (par exemple dans un domaine d'application sandbox), le niveau de confiance de l'assembly détermine s'il peut accéder au code critique du point de vue de la sécurité. Si l'assembly a un nom fort et qu'il est installé dans le Global Assembly Cache, c'est un assembly de confiance et il peut appeler des membres critiques de sécurité. Si elle n'est pas de confiance, il devient transparent même s'il n'était pas marqué comme tel, et il ne peut pas accéder aux membres critiques de sécurité.

Pour plus d’informations sur le modèle de sécurité dans .NET Framework 4, consultez [Changements relatifs à la sécurité](/previous-versions/dotnet/framework/security/security-changes).

## <a name="reflection-and-transparency"></a>Réflexion et transparence

Depuis .NET Framework 4, le common language runtime détermine le niveau de transparence d’un type ou d’un membre à partir de plusieurs facteurs, notamment le niveau de confiance de l’assembly et le niveau de confiance du domaine d’application. La réflexion fournit les propriétés <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A> et <xref:System.Type.IsSecurityTransparent%2A> pour vous permettre de connaître le niveau de transparence d'un type. Le tableau suivant montre les combinaisons valides de ces propriétés.

|Niveau de sécurité|EstCritiqueDeSécurité|EstCritiqueSécurisé|EstTransparentDeSécurité|
|--------------------|------------------------|----------------------------|---------------------------|
|Critique|`true`|`false`|`false`|
|Critique sécurisé|`true`|`true`|`false`|
|Mode transparent|`false`|`false`|`true`|

L'utilisation de ces propriétés est beaucoup plus simple que d'examiner les annotations de sécurité d'un assembly et ses types, de vérifier le niveau de confiance actuel et de tenter de dupliquer les règles du runtime. Par exemple, un même type peut être critique du point de vue de la sécurité quand il est exécuté à partir de la ligne de commande ou il peut être transparent de sécurité quand il est exécuté dans un domaine d'application sandbox.

Il existe des propriétés similaires sur les classes <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder> et <xref:System.Reflection.Emit.DynamicMethod>. (Pour d'autres abstractions de réflexion et d'émission de réflexion, des attributs de sécurité sont appliqués aux méthodes associées ; par exemple, dans le cas des propriétés, ils sont appliqués aux accesseurs de propriété.)

<a name="accessingNormallyInaccessible"></a>

## <a name="accessing-members-that-are-normally-inaccessible"></a>Accès aux membres qui sont normalement inaccessibles

Pour utiliser la réflexion pour appeler des membres inaccessibles en fonction des règles d'accessibilité du common language runtime, votre code doit disposer de l'une des deux autorisations suivantes :

- Pour permettre au code d’appeler un membre non public : votre code doit disposer de l’autorisation <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>.

  > [!NOTE]
  > Par défaut, la stratégie de sécurité refuse cette autorisation à du code provenant d'Internet. Cette autorisation ne doit jamais être accordée à du code provenant d'Internet.

- Pour permettre au code d'appeler un membre non public, pour autant que le jeu d'autorisations de l'assembly qui contient le membre appelé soit l'équivalent ou un sous-ensemble du jeu d'autorisations de l'assembly qui contient l'appel de code : votre code doit disposer de l'autorisation <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.

Par exemple, supposons que vous accordez des autorisations Internet à un domaine d'application, plus l'autorisation <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, puis que vous exécutez une application Internet avec deux assemblys, A et B.

- L'assembly A peut utiliser la réflexion pour accéder aux membres privés de l'assembly B, car le jeu d'autorisations de l'assembly B n'inclut pas d'autorisations qui n'ont pas été accordées à A.

- L’assembly A ne peut pas utiliser la réflexion pour accéder aux membres privés des assemblys du .NET Framework, comme mscorlib.dll, car mscorlib.dll est d’un niveau de confiance total et dispose donc d’autorisations qui n’ont pas été accordées à l’assembly A. Une exception <xref:System.MemberAccessException> est levée quand la sécurité d’accès du code parcourt la pile au moment de l’exécution.

## <a name="serialization"></a>Sérialisation

Pour la sérialisation, l'autorisation <xref:System.Security.Permissions.SecurityPermission> avec l'indicateur <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> permet d'obtenir et de définir des membres des types sérialisables, indépendamment de l'accessibilité. Cette autorisation permet au code de découvrir et de changer l'état privé d'une instance. (En plus de disposer des autorisations appropriées, le type doit être [marqué](../../standard/attributes/applying-attributes.md) comme étant sérialisable dans les métadonnées.)

## <a name="parameters-of-type-methodinfo"></a>Paramètres de type MethodInfo

Évitez d'écrire des membres publics qui prennent des paramètres <xref:System.Reflection.MethodInfo>, en particulier pour du code de confiance. Ces membres peuvent être plus vulnérables au code malveillant. Par exemple, considérez un membre public dans du code d'un niveau de confiance élevé qui prend un paramètre <xref:System.Reflection.MethodInfo>. Supposons que ce membre public appelle indirectement la méthode <xref:System.Reflection.MethodBase.Invoke%2A> sur le paramètre fourni. Si le membre public n'effectue pas les vérifications d'autorisations nécessaires, l'appel à la méthode <xref:System.Reflection.MethodBase.Invoke%2A> réussit toujours, car le système de sécurité détermine que l'appelant est d'un niveau de confiance élevé. Même si un code malveillant n'a pas l'autorisation d'appeler directement la méthode, il peut néanmoins le faire indirectement en appelant le membre public.

## <a name="version-information"></a>Informations sur la version

- À compter de .NET Framework 4, le code transparent ne peut pas utiliser la réflexion pour accéder aux membres critiques de sécurité.

- L’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> a été introduit dans .NET Framework 2.0 Service Pack 1. Les versions antérieures du .NET Framework exigent l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> pour le code qui utilise la réflexion pour accéder aux membres non publics. Il s'agit d'une autorisation qui ne doit jamais être accordée à du code d'un niveau de confiance partiel.

- Depuis .NET Framework 2.0, l’utilisation de la réflexion pour obtenir des informations sur les types et les membres non publics ne nécessite aucune autorisation. Dans les versions antérieures, l’autorisation <xref:System.Security.Permissions.ReflectionPermission> avec l’indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> est exigée.

## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Modifications de sécurité](/previous-versions/dotnet/framework/security/security-changes)
- [Sécurité d’accès du code](../misc/code-access-security.md)
- [Problèmes de sécurité dans l'émission de réflexion](security-issues-in-reflection-emit.md)
- [Affichage des informations de type](viewing-type-information.md)
- [Application des attributs](../../standard/attributes/applying-attributes.md)
- [Accès aux attributs personnalisés](accessing-custom-attributes.md)
