---
title: Affectation de noms forts et bibliothèques .NET
description: Meilleures pratiques recommandées pour l’affectation de noms forts aux bibliothèques .NET.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744537"
---
# <a name="strong-naming"></a>Affectation de noms forts

L’affectation de noms forts fait référence à la signature d’un assembly avec une clé, produisant un [assembly avec un nom fort](../assembly/strong-named.md). Lorsqu’un assembly a un nom fort, cela crée une identité unique basée sur le nom et le numéro de version de l’assembly, et cela peut aider à éviter les conflits de l’assembly.

L’inconvénient de l’utilisation de noms forts est que le .NET Framework sur Windows permet le chargement strict des assemblys une fois qu’un assembly possède un nom fort. Une référence d’assembly avec un nom fort doit correspondre exactement à la version référencée par un assembly, ce qui force les développeurs à [configurer des redirections de liaison](../../framework/configure-apps/redirect-assembly-versions.md) lors de l’utilisation de l’assembly :

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Lorsque les développeurs .NET se plaignent de l’affectation de noms forts, ils se plaignent généralement d’un chargement d’assembly strict. Heureusement, ce problème est limité au .NET Framework. .NET Core, Xamarin, UWP et la plupart des autres implémentations .NET n’ont pas le chargement d’assembly strict, ce qui élimine le principal inconvénient lié à l’affectation de noms forts.

Un aspect important de l’affectation de noms forts est qu’elle est virale : un assembly avec un nom fort ne peut référencer que d’autres assemblys avec un nom fort. Si votre bibliothèque n’a pas un nom fort, vous empêchez alors les développeurs qui créent une application ou une bibliothèque ayant besoin de l’affectation de noms fortsr de l’utiliser.

Les avantages de l’affectation de noms forts sont les suivants :

1. L’assembly peut être référencé et utilisé par d’autres assemblys avec un nom fort.
2. L'assembly peut être stocké dans le Global Assembly Cache (GAC).
3. L’assembly peut être chargé côte à côte avec d’autres versions de l’assembly. Le chargement des assemblys côte à côte est généralement requis par les applications avec des architectures de plug-in.

## <a name="create-strong-named-net-libraries"></a>Créer des bibliothèques .NET à nom fort

Vous devez donner à vos bibliothèques .NET open source des noms forts. L’affectation d’un nom fort à un assembly garantit que la plupart des personnes peuvent l’utiliser, et le chargement d’assembly strict affecte uniquement le .NET Framework.

> [!NOTE]
> Ce guide est spécifique aux bibliothèques .NET publiquement distribuées, telles que les bibliothèques .NET publiées sur NuGet.org. L’attribution d’un nom fort n’est pas requise par la plupart des applications .NET et ne doit pas être effectuée par défaut.

✔️ envisagez d’utiliser un nom fort pour les assemblys de votre bibliothèque.

✔️ envisagez d’ajouter la clé de nom fort à votre système de contrôle de code source.

> Une clé disponible publiquement permet aux développeurs de modifier et de recompiler le code source de votre bibliothèque avec la même clé.
>
> Vous ne devez pas rendre la clé d’affectation de noms forts publique si elle a été utilisé dans le passé pour accorder des autorisations spéciales dans des [scénarios de confiance partielle](../../framework/misc/using-libraries-from-partially-trusted-code.md). Sinon, vous pourriez compromettre les environnements existants.

> [!IMPORTANT]
> Lorsque l’identité de l’éditeur du code est requise, [Authenticode](/windows-hardware/drivers/install/authenticode) et [Signature du package NuGet](/nuget/create-packages/sign-a-package) sont recommandés. La sécurité d’accès du code (CAS) ne doit pas être utilisée comme atténuation des risques de sécurité.

✔️ envisagez d’incrémenter la version de l’assembly uniquement sur les modifications de version majeures pour aider les utilisateurs à réduire les redirections de liaison et la fréquence à laquelle elles sont mises à jour.

> En savoir plus sur [le contrôle de version et la version de l’assembly](./versioning.md#assembly-version).

❌ n’ajoutez pas, ne supprimez pas ou ne modifiez pas la clé de nom fort.

> La modification de la clé d’affectation de noms forts d’un assembly modifie l’identité de l’assembly et altère le code compilé qui l’utilise. Pour plus d'informations, consultez [Modifications importantes binaires](./breaking-changes.md#binary-breaking-change).

❌ ne publiez pas de versions avec nom fort et non avec nom fort de votre bibliothèque. Par exemple : `Contoso.Api` et `Contoso.Api.StrongNamed`.

> La publication deux packages duplique (fork) votre écosystème de développeur. En outre, si une application dépend des deux packages, le développeur peut rencontrer des conflits de noms de type. En ce qui concerne .NET, il existe des types différents dans des assemblys différents.

>[!div class="step-by-step"]
>[Précédent](cross-platform-targeting.md)
>[Suivant](nuget.md)
