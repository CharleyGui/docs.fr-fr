---
title: Redirection des versions d'assemblys
description: Rediriger les références de liaison au moment de la compilation vers différentes versions des assemblys .NET, des assemblys tiers ou des assemblys de votre propre application.
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
ms.openlocfilehash: 4cfd4336fb9999c996bea28eb86f1143932d4c51
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141732"
---
# <a name="redirecting-assembly-versions"></a>Redirection des versions d'assemblys

Vous pouvez rediriger des références de liaison de compilation vers des assemblys .NET Framework, des assemblys tiers ou des assemblys de votre propre application. Vous pouvez rediriger votre application pour utiliser une autre version d’un assembly de plusieurs manières : via une stratégie d’éditeur, un fichier de configuration d’application ou le fichier de configuration de l’ordinateur. Cet article explique comment la liaison d’assembly fonctionne dans le .NET Framework et comment la configurer.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Unification d’assembly et liaison par défaut
 Les liaisons aux assemblys .NET Framework sont parfois redirigées via un processus appelé *unification d’assembly*. Le .NET Framework est constitué d’une version du Common Language Runtime et d’environ deux douzaines d’assemblys .NET Framework qui composent la bibliothèque de types. Ces assemblys .NET Framework sont traités par le runtime comme une unité individuelle. Par défaut, lors du lancement d’une application, toutes les références à des types dans le code exécuté par le runtime sont dirigées vers les assemblys .NET Framework dont le numéro de version est identique au runtime chargé dans un processus. Les redirections qui se produisent avec ce modèle correspondent au comportement par défaut du runtime.

 Par exemple, si votre application référence des types dans l’espace de noms System.XML et a été créée à l’aide de la .NET Framework 4,5, elle contient des références statiques à l’assembly System.XML qui est fourni avec la version 4,5 du Runtime. Si vous voulez rediriger la référence de liaison pour pointer vers l’assembly System.XML livré avec .NET Framework 4, vous devez écrire des informations de redirection dans le fichier de configuration de l’application. Une redirection de liaison dans un fichier de configuration pour un assembly .NET Framework unifié annule l’unification pour cet assembly.

 En outre, vous pouvez rediriger manuellement la liaison d’assembly pour les assemblys tiers s’il existe plusieurs versions disponibles.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Redirection des versions d’assembly à l’aide d’une stratégie d’éditeur
 Les fournisseurs d’assemblys peuvent diriger les applications vers une nouvelle version d’un assembly en incluant un fichier de stratégie d’éditeur contenant le nouvel assembly. Le fichier de stratégie d’éditeur, qui se trouve dans le Global Assembly Cache, contient les paramètres de redirection d’assembly.

 Chaque version *majeure*.*mineure* d’un assembly possède son propre fichier de stratégie d’éditeur. Par exemple, les redirections de la version 2.0.2.222 vers la version 2.0.3.000 et de la version 2.0.2.321 vers 2.0.3.000 vont toutes les deux dans le même fichier, car elles sont associées à la version 2.0. Cependant, une redirection de la version 3.0.0.999 vers la version 4.0.0.000 va dans le fichier correspondant à la version 3.0.999. Chaque version majeure du .NET Framework possède son propre fichier de stratégie d’éditeur.

 S’il existe un fichier de stratégie d’éditeur pour un assembly, le runtime examine ce fichier après avoir examiné le manifeste de l’assembly et le fichier de configuration de l’application. Les fournisseurs doivent utiliser les fichiers de stratégie d’éditeur uniquement quand le nouvel assembly offre une compatibilité descendante avec l’assembly en cours de redirection.

 Vous pouvez ignorer la stratégie d’éditeur pour votre application en spécifiant des paramètres dans le fichier de configuration de l’application, comme indiqué dans la section [Contournement de la stratégie d’éditeur](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Redirection des versions d’assemblys au niveau de l’application
 Il existe différentes techniques pour modifier le comportement de liaison d’une application via le fichier de configuration d’application : vous pouvez modifier manuellement le fichier, utiliser la redirection de liaison automatique ou spécifier le comportement de liaison en ignorant la stratégie d’éditeur.

### <a name="manually-editing-the-app-config-file"></a>Modification manuelle du fichier de configuration de l’application
 Vous pouvez modifier manuellement le fichier de configuration de l’application pour résoudre les problèmes d’assembly. Par exemple, si un fournisseur peut publier une nouvelle version d’un assembly utilisé par votre application sans fournir de stratégie d’éditeur, car il ne garantit pas la compatibilité descendante, vous pouvez indiquer à votre application d’utiliser la nouvelle version de l’assembly en plaçant des informations de liaison d’assembly dans le fichier de configuration de votre application, comme suit.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Utilisation de la redirection de liaison automatique

Quand vous créez une application de bureau dans Visual Studio qui cible le .NET Framework 4.5.1 ou une version ultérieure, l’application utilise la redirection de liaison automatique. Cela signifie que si deux composants référencent des versions différentes d’un même assembly avec nom fort, le runtime ajoute automatiquement une redirection de liaison vers la version la plus récente de l’assembly dans le fichier de configuration d’application de sortie (app.config). Cette redirection remplace l’unification d’assemblys qui pourrait se produire autrement. Le fichier source app.config n'est pas modifié. Par exemple, supposons que votre application référence directement un composant .NET Framework hors plage mais utilise une bibliothèque tierce qui cible une version antérieure du même composant. Lorsque vous compilez l’application, le fichier de configuration de l’application de sortie est modifié pour inclure une redirection de liaison vers la version plus récente du composant. Si vous créez une application web, vous recevez un avertissement de génération concernant le conflit de liaison, qui, à son tour, vous donne la possibilité d’ajouter la redirection de liaison nécessaire au fichier de configuration web source.

Si vous ajoutez manuellement des redirections de liaison au fichier de app.config source, au moment de la compilation, Visual Studio tente d’unifier les assemblys en fonction des redirections de liaison que vous avez ajoutées. Par exemple, supposons que vous insérez la redirection de liaison suivantes pour un assembly :

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Si un autre projet dans votre application référence la version 1.0.0.0 du même assembly, la redirection de liaison automatique ajoute l’entrée suivante au fichier app.config de sortie afin que l’application soit unifiée sur la version 2.0.0.0 de cet assembly :

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Vous pouvez activer la redirection de liaison automatique si votre application cible des versions antérieures du .NET Framework. Vous pouvez substituer ce comportement par défaut en fournissant des informations de redirection de liaison dans le fichier de app.config pour n’importe quel assembly, ou en désactivant la fonctionnalité de redirection de liaison. Pour plus d’informations sur la façon d’activer ou de désactiver cette fonctionnalité, consultez [Comment : activer et désactiver la redirection de liaison automatique](how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Contournement de la stratégie d’éditeur
 Vous pouvez remplacer la stratégie d’éditeur dans le fichier de configuration d’application, si nécessaire. Par exemple, les nouvelles versions d’assemblys se déclarant à compatibilité descendante peuvent quand même bloquer une application. Si vous souhaitez ignorer la stratégie d’éditeur, ajoutez [\<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) un élément à [\<dependentAssembly>](./file-schema/runtime/dependentassembly-element.md) l’élément dans le fichier de configuration d’application et définissez l’attribut **apply** sur **no**, qui remplace tous les paramètres **Yes** précédents.

 `<publisherPolicy apply="no" />`

 Contournez la stratégie d’éditeur pour assurer le fonctionnement de votre application pour vos utilisateurs, mais veillez néanmoins à signaler le problème au fournisseur de l’assembly. Si un assembly possède un fichier de stratégie d’éditeur, le fournisseur doit s’assurer que l’assembly est à compatibilité descendante et que les clients peuvent utiliser la nouvelle version autant que possible.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Redirection des versions d’assemblys au niveau de l’ordinateur
 Dans certains cas rares, l’administrateur de l’ordinateur peut souhaiter que toutes les applications d’un ordinateur utilisent une version spécifique d’un assembly. Par exemple, l’administrateur peut vouloir que toutes les applications utilisent une certaine version d’assembly, car cette version corrige une brèche de sécurité. Si un assembly est redirigé dans le fichier de configuration de l’ordinateur, toutes les applications de cet ordinateur qui utilisent l’ancienne version sont redirigées pour utiliser la nouvelle version. Le fichier de configuration de l’ordinateur remplace le fichier de configuration d’application et le fichier de stratégie d’éditeur. Ce fichier se trouve dans le répertoire %*chemin d'installation du runtime*%\Config. En règle générale, le .NET Framework est installé dans le répertoire %drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Spécification d’une liaison d’assembly dans les fichiers de configuration
 Le même format XML vous permet de spécifier les redirections de liaison, que ce soit dans le fichier de configuration d’application, dans le fichier de configuration de l’ordinateur ou dans le fichier de stratégie d’éditeur. Pour rediriger une version d’assembly vers une autre, utilisez l' [\<bindingRedirect>](./file-schema/runtime/bindingredirect-element.md) élément. L’attribut **oldVersion** permet de spécifier une version d’assembly unique ou une plage de versions. L’attribut `newVersion` doit spécifier une version unique.  Par exemple, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` spécifie que le runtime doit utiliser la version 2.0.0.0 au lieu des versions d’assembly comprises entre 1.1.0.0 et 1.2.0.0.

 L’exemple de code suivant montre divers scénarios de redirection de liaison. Cet exemple spécifie une redirection pour une plage de versions pour `myAssembly`, et une redirection de liaison unique pour `mySecondAssembly`. L’exemple spécifie également que le fichier de stratégie d’éditeur ne doit pas remplacer les redirections de liaison pour `myThirdAssembly`.

 Pour lier un assembly, vous devez spécifier la chaîne "urn : schemas-microsoft-com : ASM. v1" avec l’attribut **xmlns** dans la [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) balise.

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Limitation des liaisons d’assembly à une version spécifique
 Vous pouvez utiliser l’attribut **appliesTo** sur l' [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) élément dans un fichier de configuration d’application pour rediriger les références de liaison d’assembly vers une version spécifique du .NET Framework. Cet attribut facultatif utilise un numéro de version .NET Framework pour indiquer la version à laquelle il s'applique. Si aucun attribut **appliesTo** n’est spécifié, l' [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) élément s’applique à toutes les versions du .NET Framework.

 Par exemple, pour rediriger la liaison d’assembly pour un assembly .NET Framework 3.5, vous devez inclure le code XML suivant dans le fichier de configuration d’application.

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 Vous devez entrer les informations de redirection dans l’ordre des versions. Par exemple, entrez les informations de redirection de liaison d’assembly pour les assemblys .NET Framework 3.5 suivies de celles pour les assemblys .NET Framework 4.5. Enfin, vous devez entrer les informations de redirection des liaisons d'assembly pour toutes les redirections d'assembly du .NET Framework qui n'utilisent pas d'attribut **appliesTo** et qui s'appliquent donc à toutes les versions du .NET Framework. En cas de conflit de redirection, la première instruction de redirection correspondante dans le fichier de configuration est utilisée.

 Par exemple, pour rediriger une référence à un assembly .NET Framework 3.5 et une autre à un assembly .NET Framework 4, utilisez le modèle indiqué dans le pseudo-code suivant.

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>Voir aussi

- [Procédure : Activer et désactiver la redirection de liaison automatique](how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect>Appartient](./file-schema/runtime/bindingredirect-element.md)
- [Autorisation de sécurité pour la redirection de liaison d’assembly](assembly-binding-redirection-security-permission.md)
- [Assemblys dans .NET](../../standard/assembly/index.md)
- [Programmation à l’aide d’assemblys](../../standard/assembly/index.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration d’applications](index.md)
- [Schéma des paramètres d’exécution](./file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](./file-schema/index.md)
- [Procédure : Créer une stratégie d’éditeur](how-to-create-a-publisher-policy.md)
