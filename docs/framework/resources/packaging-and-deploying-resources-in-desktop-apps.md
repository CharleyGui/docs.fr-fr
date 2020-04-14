---
title: Packager et déployer des ressources dans des applications .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
ms.openlocfilehash: d64e3b5201e34541fdafa5724b0c7e8c3f6c0c0d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243048"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Packager et déployer des ressources dans des applications .NET

Les applications s’appuient sur le gestionnaire des ressources du .NET Framework, représenté par la classe <xref:System.Resources.ResourceManager>, pour récupérer des ressources localisées. Le gestionnaire des ressources suppose qu’un modèle Hub and Spoke est utilisé pour empaqueter et déployer des ressources. Le hub est l’assembly principal qui contient le code exécutable non localisable et les ressources pour une culture unique, appelée culture neutre ou par défaut. La culture par défaut est la culture de secours de l’application ; il s’agit de la culture dont les ressources sont utilisées si aucune ressource localisée ne peut être trouvée. Chaque spoke se connecte à un assembly satellite qui contient les ressources d’une culture unique, mais ne contient pas de code.

Ce modèle présente plusieurs avantages :

- Vous pouvez ajouter de façon incrémentielle des ressources pour de nouvelles cultures après avoir déployé une application. Comme le développement ultérieur de ressources spécifiques à une culture peut nécessiter du temps, cela vous permet de libérer d’abord votre application principale, puis de proposer des ressources spécifiques à une culture ultérieurement.
- Vous pouvez mettre à jour et changer les assemblys satellites d’une application sans recompiler l’application.
- Une application doit charger uniquement les assemblys satellites qui contiennent les ressources nécessaires pour une culture particulière. Cela peut réduire considérablement l’utilisation des ressources système.

 Cependant, ce modèle présente également des inconvénients :

- Vous devez gérer plusieurs ensembles de ressources.
- Le coût initial du test d’une application augmente, car vous devez tester plusieurs configurations. À longue échéance, il sera plus facile et moins coûteux de tester une application principale et plusieurs satellites que de tester et de tenir à jour en parallèle plusieurs versions internationales.

## <a name="resource-naming-conventions"></a>Conventions de nommage des ressources

Quand vous empaquetez les ressources de votre application, vous devez les nommer en utilisant les conventions d’affectation de noms pour les ressources que le Common Language Runtime attend. Le runtime identifie une ressource par son nom de culture. Chaque culture a un nom unique, qui est en général une combinaison d’un nom de culture à deux lettres en minuscules associé à une langue et, si nécessaire, un nom de sous-culture à deux lettres en majuscules associé à un pays ou une région. Le nom de la sous-culture suit le nom de la culture, séparés par un tiret (-). Les exemples incluent ja-JP pour le japonais tel qu’il est parlé au Japon, en-US pour l’anglais tel qu’il est parlé aux États-Unis, de-DE pour l’allemand tel qu’il est parlé en Allemagne ou de-AT pour l’allemand tel qu’il est parlé en Autriche. Consultez la colonne **Balise de langue** dans la [liste des noms de langue/région pris en charge par Windows](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c). Les noms de culture respectent la norme définie par [BCP 47](https://tools.ietf.org/html/bcp47).

> [!NOTE]
> Il y a quelques exceptions pour les `zh-Hans` noms de culture de deux lettres, comme pour le chinois (simplifié).

> [!NOTE]
> Pour plus d’informations sur la création de fichiers de ressources, consultez [Création de fichiers de ressources](creating-resource-files-for-desktop-apps.md) et [Création d’assemblys satellites](creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Processus de secours pour les ressources

Le modèle Hub and Spoke pour l’empaquetage et le déploiement de ressources utilise un processus de secours pour localiser les ressources appropriées. Si l’utilisateur d’une application demande une ressource localisée qui n’est pas disponible, le Common Language Runtime recherche dans la hiérarchie des cultures une ressource de secours appropriée, la plus proche de celle demandée par l’utilisateur, et lève une exception uniquement en dernier ressort. À chaque niveau de la hiérarchie, si une ressource appropriée est trouvée, le runtime l’utilise. Si la ressource est introuvable, la recherche se poursuit au niveau suivant.

Pour améliorer les performances de recherche, appliquez l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> à votre assembly principal et passez-lui le nom de la langue neutre à utiliser avec votre assembly principal.

### <a name="net-framework-resource-fallback-process"></a>Processus de secours pour les ressources .NET Framework

Le processus de secours pour les ressources .NET Framework comprend les étapes suivantes :

> [!TIP]
> Vous pouvez être en mesure d’utiliser [ \<l’élément relativeBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) configuration pour optimiser le processus de repli des ressources et le processus par lequel les sondes de temps d’exécution pour les assemblages de ressources. Pour plus d’informations, consultez la section [Optimisation du processus de secours pour les ressources](packaging-and-deploying-resources-in-desktop-apps.md#Optimizing).

1. Le runtime recherche d’abord dans le [Global Assembly Cache](../app-domains/gac.md) un assembly qui correspond à la culture demandée pour votre application.

     Le Global Assembly Cache peut stocker des assemblys de ressources partagés par de nombreuses applications. Cela vous évite d’avoir à inclure des ensembles de ressources spécifiques dans la structure de répertoires de chaque application que vous créez. Si le runtime trouve une référence à l’assembly, il recherche la ressource demandée dans cet assembly. S’il trouve l’entrée dans l’assembly, il utilise la ressource demandée. S’il ne trouve pas l’entrée, il continue la recherche.

2. Le runtime recherche ensuite un sous-répertoire correspondant à la culture demandée dans le répertoire de l’assembly en cours d’exécution. S’il le trouve, il y recherche un assembly satellite valide pour la culture demandée. Le runtime recherche ensuite dans l’assembly satellite la ressource demandée. S’il trouve la ressource dans l’assembly, il l’utilise. S’il ne trouve pas la ressource, il continue la recherche.

3. Le runtime interroge ensuite Windows Installer pour déterminer si l’assembly satellite doit être installé à la demande. Dans ce cas, il gère l’installation, charge l’assembly et y recherche la ressource demandée. S’il trouve la ressource dans l’assembly, il l’utilise. S’il ne trouve pas la ressource, il continue la recherche.

4. Le runtime déclenche l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pour indiquer qu’il lui est impossible de trouver l’assembly satellite. Si vous choisissez de gérer l’événement, le gestionnaire d’événements peut retourner une référence à l’assembly satellite dont les ressources seront utilisées pour la recherche. Sinon, le gestionnaire d’événements retourne `null` et la recherche se poursuit.

5. Le runtime effectue ensuite une nouvelle recherche dans le Global Assembly Cache, cette fois pour trouver l’assembly parent de la culture demandée. Si l’assembly parent existe dans le Global Assembly Cache, le runtime recherche la ressource demandée dans cet assembly.

     La culture parente est définie comme culture de secours appropriée. Considérez les parents comme des candidats de secours, car n’importe quelle ressource est préférable à la levée d’une exception. Ce processus vous permet également de réutiliser les ressources. Vous devez inclure une ressource donnée au niveau parent uniquement si la culture enfant n’a pas besoin de localiser la ressource demandée. Par exemple, si vous fournissez des assemblys satellites pour `en` (anglais neutre), `en-GB` (anglais du Royaume-Uni) et `en-US` (anglais des États-Unis), le satellite `en` contient la terminologie commune et les satellites `en-GB` et `en-US` une terminologie de remplacement, seulement pour les termes qui diffèrent.

6. Le runtime vérifie ensuite le répertoire de l’assembly en cours d’exécution à la recherche d’un répertoire parent. Si un répertoire parent existe, le runtime y recherche un assembly satellite valide pour la culture parente. S’il trouve l’assembly, le runtime y recherche la ressource demandée. S’il trouve la ressource, il l’utilise. S’il ne trouve pas la ressource, il continue la recherche.

7. Le runtime interroge ensuite Windows Installer pour déterminer si l’assembly satellite parent doit être installé à la demande. Dans ce cas, il gère l’installation, charge l’assembly et y recherche la ressource demandée. S’il trouve la ressource dans l’assembly, il l’utilise. S’il ne trouve pas la ressource, il continue la recherche.

8. Le runtime déclenche l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pour indiquer qu’il lui est impossible de trouver une ressource de secours appropriée. Si vous choisissez de gérer l’événement, le gestionnaire d’événements peut retourner une référence à l’assembly satellite dont les ressources seront utilisées pour la recherche. Sinon, le gestionnaire d’événements retourne `null` et la recherche se poursuit.

9. Le runtime effectue ensuite des recherches dans les assemblys parents, comme aux trois étapes précédentes, dans les différents niveaux. Chaque culture n’a qu’un seul parent, qui est défini par la propriété <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>, mais un parent peut avoir son propre parent. La recherche des cultures parentes s’arrête quand la propriété <xref:System.Globalization.CultureInfo.Parent%2A> d’une culture retourne <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ; pour la culture de secours pour les ressources, la culture indifférente n’est pas considérée comme une culture parente ou une culture qui peut avoir des ressources.

10. Si la culture spécifiée à l’origine et tous les parents ont fait l’objet de la recherche et que la ressource est toujours introuvable, la ressource de la culture par défaut (de secours) est utilisée. En règle générale, les ressources de la culture par défaut sont incluses dans l’assembly d’application principal. Toutefois, vous pouvez spécifier la valeur <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> pour la propriété <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> de l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour indiquer que l’emplacement de secours ultime pour les ressources est un assembly satellite, plutôt que l’assembly principal.

    > [!NOTE]
    > La ressource par défaut est la seule ressource qui peut être compilée avec l’assembly principal. Sauf si vous spécifiez un assembly satellite à l’aide de l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute>, il s’agit du secours ultime (parent final). Par conséquent, nous vous recommandons de toujours inclure un ensemble de ressources par défaut dans votre assembly principal. Vous empêchez ainsi la levée d’exceptions. En ajoutant un fichier de ressources par défaut, vous fournissez une solution de secours pour toutes les ressources et garantissez qu’au moins une ressource est toujours présente pour l’utilisateur, même si elle n’est pas propre à une culture.

11. Enfin, si le runtime ne trouve pas une ressource pour une culture par défaut (de secours), une exception <xref:System.Resources.MissingManifestResourceException> ou <xref:System.Resources.MissingSatelliteAssemblyException> est levée pour indiquer que la ressource est introuvable.

Supposons par exemple que l’application demande une ressource localisée en espagnol (Mexique) (la culture `es-MX`). Tout d’abord, le runtime recherche l’assembly correspondant à `es-MX` dans le Global Assembly Cache, mais ne le trouve pas. Il recherche ensuite un répertoire `es-MX` dans le répertoire de l’assembly en cours d’exécution. En cas d’échec, il effectue une nouvelle recherche dans le Global Assembly Cache pour trouver un assembly parent qui reflète la culture de secours correspondante, ici `es` (espagnol). S’il ne trouve pas l’assembly parent, le runtime fouille tous les niveaux potentiels des assemblys parents, à la recherche de la culture `es-MX`, jusqu’à ce qu’il trouve une ressource correspondante. Si aucune ressource n’est trouvée, le runtime utilise la ressource pour la culture par défaut.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>Optimiser le processus de secours pour les ressources .NET Framework

Dans les conditions suivantes, vous pouvez optimiser le processus par lequel le runtime recherche des ressources dans les assemblys satellites.

- Les assemblys satellites sont déployés au même emplacement que l’assembly de code. Si l’assembly de code est installé dans le [Global Assembly Cache](../app-domains/gac.md), les assemblys satellites sont également installés dans le Global Assembly Cache. Si l’assembly de code est installé dans un répertoire, les assemblys satellites sont installés dans des dossiers spécifiques à la culture de ce répertoire.

- Les assemblys satellites ne sont pas installés à la demande.

- Le code d’application ne gère pas l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

Vous optimisez la sonde pour les assemblages de satellites en incluant les `enabled` `true` [ \<relativeBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) élément et en définissant son attribut dans le fichier de configuration d’application, comme indiqué dans l’exemple suivant.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

La recherche optimisée des assemblys satellites est une fonctionnalité d’abonnement. Autrement dit, le runtime suit la procédure décrite dans [Processus de secours pour les ressources](packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1), sauf si l’élément [\<relativeBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) est présent dans le fichier de configuration de l’application et que son attribut `enabled` a la valeur `true`. Dans ce cas, le processus de recherche d’un assembly satellite est modifié comme suit :

- Le runtime utilise l’emplacement de l’assembly de code parent pour rechercher l’assembly satellite. Si l’assembly parent est installé dans le Global Assembly Cache, le runtime effectue la recherche dans le cache, mais pas dans le répertoire de l’application. Si l’assembly parent est installé dans un répertoire de l’application, le runtime effectue la recherche dans le répertoire de l’application, mais pas dans le Global Assembly Cache.

- Le runtime n’interroge pas Windows Installer pour l’installation à la demande des assemblys satellites.

- Si la recherche d’un assembly de ressource particulier échoue, le runtime ne déclenche pas l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

### <a name="net-core-resource-fallback-process"></a>Processus de secours pour les ressources .NET Core

Le processus de secours pour les ressources .NET Core comprend les étapes suivantes :

1. Le runtime tente de charger un assembly satellite pour la culture demandée.
     - Il recherche un sous-répertoire correspondant à la culture demandée dans le répertoire de l’assembly en cours d’exécution. S’il le trouve, il y recherche un assembly satellite valide pour la culture demandée et le charge.

       > [!NOTE]
       > Sur les systèmes d’exploitation dont le système de fichiers respecte la casse (autrement dit, Linux et macOS), la recherche d’un sous-répertoire du nom de la culture est sensible à la casse. La casse du nom du sous-répertoire doit être identique à celle de <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (par exemple, `es` ou `es-MX`).

       > [!NOTE]
       > Si le programmeur a dérivé un contexte de chargement d’assembly personnalisé à partir de <xref:System.Runtime.Loader.AssemblyLoadContext>, la situation est complexe. Si l’assembly en cours d’exécution a été chargé dans le contexte personnalisé, le runtime charge l’assembly satellite dans le contexte personnalisé. Ce document ne couvre pas ce processus en détail. Consultez <xref:System.Runtime.Loader.AssemblyLoadContext>.

     - S’il n’a pas trouvé l’assembly satellite, <xref:System.Runtime.Loader.AssemblyLoadContext> déclenche l’événement <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> pour le signaler. Si vous choisissez de gérer l’événement, votre gestionnaire d’événements peut charger et retourner une référence à l’assembly satellite.
     - Si l’assembly satellite reste introuvable, AssemblyLoadContext conduit AppDomain à déclencher un événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pour le signaler. Si vous choisissez de gérer l’événement, votre gestionnaire d’événements peut charger et retourner une référence à l’assembly satellite.

2. Dès qu’il trouve un assembly satellite, le runtime y recherche la ressource demandée. S’il trouve la ressource dans l’assembly, il l’utilise. S’il ne trouve pas la ressource, il continue la recherche.

     > [!NOTE]
     > Pour trouver une ressource dans l’assembly satellite, le runtime recherche le fichier de ressources demandé par <xref:System.Resources.ResourceManager> pour <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. Dans le fichier de ressources, il cherche le nom de la ressource demandée. En cas d’échec, la ressource est traitée comme introuvable.

3. Le runtime parcourt ensuite les assemblys de culture parente à différents niveaux potentiels, en répétant à chaque fois les étapes 1 et 2.

     La culture parente est définie comme une culture de secours appropriée. Considérez les parents comme des candidats de secours, car n’importe quelle ressource est préférable à la levée d’une exception. Ce processus vous permet également de réutiliser les ressources. Vous devez inclure une ressource donnée au niveau parent uniquement si la culture enfant n’a pas besoin de localiser la ressource demandée. Par exemple, si vous fournissez des assemblys satellites pour `en` (anglais neutre), `en-GB` (anglais du Royaume-Uni) et `en-US` (anglais des États-Unis), le satellite `en` contient la terminologie commune et les satellites `en-GB` et `en-US` une terminologie de remplacement, seulement pour les termes qui diffèrent.

     Chaque culture n’a qu’un seul parent, qui est défini par la propriété <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>, mais un parent peut avoir son propre parent. La recherche des cultures parentes s’arrête lorsque la propriété <xref:System.Globalization.CultureInfo.Parent%2A> d’une culture retourne <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. En ce qui concerne la culture de secours pour les ressources, la culture invariante n’est pas considérée comme une culture parente ou une culture pouvant comporter des ressources.

4. Si la culture spécifiée à l’origine et tous les parents ont fait l’objet de la recherche et que la ressource est toujours introuvable, la ressource de la culture par défaut (de secours) est utilisée. En règle générale, les ressources de la culture par défaut sont incluses dans l’assembly d’application principal. Toutefois, vous pouvez spécifier la valeur <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> pour la propriété <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> afin d’indiquer que l’emplacement de secours ultime des ressources est un assembly satellite, plutôt que l’assembly principal.

    > [!NOTE]
    > La ressource par défaut est la seule ressource qui peut être compilée avec l’assembly principal. Sauf si vous spécifiez un assembly satellite à l’aide de l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute>, il s’agit du secours ultime (parent final). Par conséquent, nous vous recommandons de toujours inclure un ensemble de ressources par défaut dans votre assembly principal. Vous empêchez ainsi la levée d’exceptions. En ajoutant un fichier de ressources par défaut, vous fournissez une solution de secours pour toutes les ressources et garantissez qu’au moins une ressource est toujours présente pour l’utilisateur, même si elle n’est pas propre à une culture.

5. Enfin, si le runtime ne trouve pas de fichier de ressources pour une culture (de secours) par défaut, une exception <xref:System.Resources.MissingManifestResourceException> ou <xref:System.Resources.MissingSatelliteAssemblyException> est levée pour indiquer que la ressource est introuvable. Si le fichier de ressources est trouvé, mais que la ressource demandée n’est pas présente, la demande retourne `null`.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Secours ultime pour l’assembly satellite

Vous pouvez éventuellement supprimer des ressources de l’assembly principal et spécifier que le runtime doit charger les ressources de secours ultime depuis un assembly satellite qui correspond à une culture spécifique. Pour contrôler le processus de secours, vous utilisez le constructeur <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29> et fournissez une valeur pour le paramètre <xref:System.Resources.UltimateResourceFallbackLocation> qui spécifie si le gestionnaire des ressources doit extraire les ressources de secours à partir de l’assembly principal ou d’un assembly satellite.

L’exemple .NET Framework suivant utilise l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour stocker les ressources de secours d’une application dans un assembly satellite pour la langue française (`fr`). L’exemple comprend deux fichiers de ressources textuels qui définissent une ressource de type chaîne unique nommée `Greeting`. Le premier, resources.fr.txt, contient une ressource de langue française.

```text
Greeting=Bon jour!
```

Le second, resources.ru.txt, contient une ressource de langue russe.

```text
Greeting=Добрый день
```

Ces deux fichiers sont compilés en fichiers .resources en exécutant le [Générateur de fichiers de ressources (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) à partir de la ligne de commande. Pour la ressource de langue française, la commande est :

**resgen.exe resources.fr.txt**

Pour la ressource de langue russe, la commande est :

**resgen.exe resources.ru.txt**

Les fichiers .resources sont incorporés dans des bibliothèques de liens dynamiques en exécutant [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) à partir de la commande de ligne pour la ressource de langue française comme suit :

**al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**

et pour la ressource de langue russe comme suit :

**al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**

Le code source de l’application réside dans un fichier nommé Example1.cs ou Example1.vb. Il inclut l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour indiquer que la ressource d’application par défaut se trouve dans le sous-répertoire fr. Il instancie le gestionnaire des ressources, récupère la valeur de la ressource `Greeting` et l’affiche dans la console.

[!code-csharp[Conceptual.Resources.Packaging#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Vous pouvez ensuite compiler le code source C# à partir de la ligne de commande comme suit :

```console
csc Example1.cs
```

La commande pour le compilateur Visual Basic est très semblable :

```console
vbc Example1.vb
```

Comme aucune ressource n’est incorporée dans l’assembly principal, il est inutile de compiler à l’aide du commutateur `/resource`.

Quand vous exécutez l’exemple à partir d’un système dont la langue est autre que le russe, la sortie suivante s’affiche :

```output
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Autre empaquetage suggéré

Des contraintes de temps ou de budget peuvent vous empêcher de créer un ensemble de ressources pour chaque sous-culture que votre application prend en charge. À la place, vous pouvez créer un seul assembly satellite pour une culture parente qui peut être utilisé par toutes les sous-cultures apparentées. Par exemple, vous pouvez fournir un seul assembly satellite anglais (en) qui est récupéré par les utilisateurs qui demandent des ressources anglaises spécifiques à une région et un seul assembly satellite allemand (de) pour les utilisateurs qui demandent des ressources allemandes spécifiques à une région. Par exemple, les demandes pour l’allemand tel qu’il est parlé en Allemagne (de-DE), en Autriche (de-AT) et en Suisse (de-CH) reviennent à l’assembly satellite allemand (de). Comme les ressources par défaut représentent les ressources de secours final et doivent dont être les ressources qui seront demandées par la majorité des utilisateurs de votre application, choisissez-les avec précaution. Cette solution déploie des ressources qui sont moins spécifiques à une culture, mais peut réduire de manière significative les coûts de localisation de votre application.

## <a name="see-also"></a>Voir aussi

- [Ressources dans les applications de bureau](index.md)
- [Cache de l’Assemblée mondiale](../app-domains/gac.md)
- [Création de fichiers de ressources](creating-resource-files-for-desktop-apps.md)
- [Création d’assemblys satellites](creating-satellite-assemblies-for-desktop-apps.md)
