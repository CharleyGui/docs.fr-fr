---
title: Méthode de localisation des assemblys par le runtime
description: Découvrez comment le common language runtime (CLR) localise et lie les assemblys qui composent votre application dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
ms.openlocfilehash: 1b2ee58ccbd4bdfceb6300c20d5255718982f2e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272525"
---
# <a name="how-the-runtime-locates-assemblies"></a>Méthode de localisation des assemblys par le runtime

Pour déployer correctement votre application .NET Framework, il est important de bien comprendre comment le common language runtime localise les assemblys qui composent votre application et comment il établit des liaisons à ces assemblys. Par défaut, le runtime essaie d'établir une liaison avec la version exacte d'un assembly avec lequel l'application a été générée. Ce comportement par défaut peut être substitué par les paramètres du fichier de configuration.

Le common language runtime effectue plusieurs étapes pour essayer de localiser un assembly et résoudre une référence d'assembly. Chaque étape est expliquée dans les sections ci-dessous. Le terme « détection » est souvent utilisé pour décrire la manière dont le runtime localise les assemblys. Il fait référence au jeu de paramètres heuristiques utilisé pour localiser l'assembly en fonction de son nom et de sa culture.

> [!NOTE]
> Vous pouvez afficher les informations de liaison du fichier journal en utilisant la [visionneuse du journal de liaison d’assembly (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), fournie dans le SDK Windows.

## <a name="initiating-the-bind"></a>Initiation de la liaison

Le processus de localisation et de liaison d'un assembly débute quand le runtime tente de résoudre une référence à un autre assembly. Cette référence peut être statique ou dynamique. Le compilateur enregistre les références statiques dans les métadonnées du manifeste d'assembly au moment de la build. Les références dynamiques sont créées instantanément après l’appel à différentes méthodes, telles que <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.

La meilleure façon de référencer un assembly est d'utiliser une référence complète, comprenant le nom de l'assembly, sa version, sa culture et son jeton de clé publique (le cas échéant). Le runtime se sert de ces informations pour localiser l'assembly, en suivant les étapes décrites plus loin dans cette section. Il utilise le même processus de résolution pour les références d'assemblys statiques et dynamiques.

Vous pouvez aussi créer une référence dynamique à un assembly en fournissant à la méthode d'appel seulement une partie des informations relatives à l'assembly, par exemple en spécifiant le nom de l'assembly uniquement. Dans ce cas, l'assembly n'est recherché que dans le répertoire de l'application et aucune autre vérification n'est effectuée. Il est possible de créer une référence partielle à l’aide d’une des méthodes de chargement des assemblys, telle que <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.

Enfin, vous pouvez créer une référence dynamique à l’aide d’une méthode telle que <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> et fournir uniquement des informations partielles. vous qualifiez ensuite la référence à l’aide [\<qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) de l’élément dans le fichier de configuration de l’application. Cet élément vous permet de fournir les informations de la référence complète (nom, version, culture et, le cas échéant, jeton de clé publique) dans le fichier de configuration de votre application plutôt que dans votre code. Utilisez cette technique si vous souhaitez créer une référence complète à un assembly en dehors du répertoire de l'application, ou si vous souhaitez référencer un assembly dans le Global Assembly Cache en gardant la possibilité de spécifier la référence complète dans le fichier de configuration plutôt que dans votre code.

> [!NOTE]
> Ce type de référence partielle ne doit pas être utilisé avec des assemblys partagés par plusieurs applications. Les paramètres de configuration sont appliqués au niveau de l'application, et non de chaque assembly. Par conséquent, un assembly partagé utilisant ce type de référence partielle nécessite que chaque application liée à l'assembly partagé possède les informations de qualification dans son fichier de configuration.

Le runtime effectue les étapes suivantes pour résoudre une référence d'assembly :

1. Il[détermine la version correcte de l'assembly](#step1) en examinant les fichiers de configuration applicables, y compris le fichier de configuration de l'application, le fichier de stratégie d'éditeur et le fichier de configuration de l'ordinateur. Si le fichier de configuration est situé sur un ordinateur distant, le runtime doit tout d'abord localiser et télécharger le fichier de configuration de l'application.

2. Il[vérifie si le nom de l'assembly a déjà été lié](#step2) et, si c'est le cas, il utilise l'assembly précédemment chargé. Si une précédente demande de chargement de l'assembly avait échoué, la nouvelle demande échoue immédiatement sans qu'aucune tentative de chargement de l'assembly ne soit effectuée.

    > [!NOTE]
    > La mise en cache des échecs de liaison d'assemblys a été introduite dans .NET Framework version 2.0.

3. Il[vérifie le Global Assembly Cache](#step3). S'il y trouve l'assembly, il l'utilise.

4. Il[détecte l'assembly](#step4) en procédant comme suit :

    1. Si la configuration et la stratégie d'éditeur n'affectent pas la référence d'origine et que la demande de liaison a été faite avec la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> , le runtime vérifie la présence d'indications relatives à l'emplacement.

    2. Si une base de code est trouvée dans les fichiers de configuration, le runtime vérifie uniquement cet emplacement. Si cette détection ne donne aucun résultat, le runtime détermine que la demande de liaison a échoué et ne tente pas d'autre détection.

    3. Il détecte l'assembly en se servant des paramètres heuristiques décrits dans la [section sur la détection](#step4). Si la détection ne permet pas de trouver l'assembly, le runtime demande à Windows Installer de lui fournir l'assembly (sous la forme d'une fonctionnalité d'installation à la demande).

        > [!NOTE]
        > Pour les assemblys sans nom fort, le runtime n'effectue pas de vérification de version, ni de vérification dans le Global Assembly Cache.

<a name="step1"></a>

## <a name="step-1-examining-the-configuration-files"></a>Étape 1 : examen des fichiers de configuration

Le comportement de la liaison d'assembly peut être configuré à différents niveaux à l'aide de ces trois fichiers XML :

- le fichier de configuration de l'application ;

- le fichier de stratégie d'éditeur ;

- le fichier de configuration de l'ordinateur.

Ces fichiers utilisent la même syntaxe. Ils fournissent plusieurs informations, notamment les redirections de liaisons, l'emplacement du code et les modes de liaison pour des assemblys particuliers. Chaque fichier de configuration peut contenir un [ \<assemblyBinding> élément](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) qui redirige le processus de liaison. Les éléments enfants de l' [ \<assemblyBinding> élément](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) incluent l' [ \<dependentAssembly> élément](../configure-apps/file-schema/runtime/dependentassembly-element.md). Les enfants de l' [ \<dependentAssembly> élément](../configure-apps/file-schema/runtime/dependentassembly-element.md) incluent l' [ \<assemblyIdentity> élément](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), l' [ \<bindingRedirect> élément](../configure-apps/file-schema/runtime/bindingredirect-element.md)et l' [ \<codeBase> élément](../configure-apps/file-schema/runtime/codebase-element.md).

> [!NOTE]
> Les trois fichiers de configuration peuvent contenir des informations de configuration, mais ils n'acceptent pas forcément tous les éléments. Par exemple, les informations sur le mode de liaison et le chemin d'accès privé peuvent seulement se trouver dans le fichier de configuration de l'application. Pour obtenir la liste complète des informations contenues dans chaque fichier, consultez [Configuration des applications à l'aide de fichiers de configuration](../configure-apps/index.md).

### <a name="application-configuration-file"></a>Fichier de configuration de l'application

Le common language runtime vérifie tout d'abord le fichier de configuration de l'application à la recherche d'informations qui substituent les informations de version stockées dans le manifeste de l'assembly appelant. Le fichier de configuration de l'application peut être déployé avec une application, mais il n'est pas nécessaire à l'exécution de celle-ci. En règle générale, la récupération de ce fichier est quasi instantanée mais, si la base de l'application se trouve sur un ordinateur distant (dans le cas d'une application web basée sur Internet Explorer, par exemple), le fichier de configuration doit être téléchargé.

Pour les fichiers exécutables client, le fichier de configuration de l'application réside dans le même répertoire que le fichier exécutable de l'application et possède le même nom que le fichier exécutable avec une extension .config. Par exemple, le fichier de configuration de C:\Program Files\Myapp\Myapp.exe est C:\Program Files\Myapp\Myapp.exe.config. Dans un scénario basé sur un navigateur, le fichier HTML doit utiliser l' **\<link>** élément pour pointer explicitement vers le fichier de configuration.

Le code suivant fournit un exemple simple de fichier de configuration de l'application. Cet exemple ajoute un élément <xref:System.Diagnostics.TextWriterTraceListener> à la collection <xref:System.Diagnostics.Debug.Listeners%2A> pour activer l'enregistrement des informations de débogage dans un fichier.

```xml
<configuration>
   <system.diagnostics>
      <trace useGlobalLock="false" autoflush="true" indentsize="0">
         <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
         </listeners>
      </trace>
   </system.diagnostics>
</configuration>
```

### <a name="publisher-policy-file"></a>Fichier de stratégie d'éditeur

Le runtime examine ensuite le fichier de stratégie d'éditeur (si ce fichier existe). Les fichiers de stratégie d'éditeur sont distribués par un éditeur de composant, sous forme de correctif ou de mise à jour, à un composant partagé. Ces fichiers contiennent des informations de compatibilité émises par l'éditeur du composant partagé qui dirige une référence d'assembly vers une nouvelle version. Contrairement aux fichiers de configuration de l'application et de l'ordinateur, les fichiers de stratégie d'éditeur sont contenus dans leur propre assembly qui doit être installé dans le Global Assembly Cache.

Voici un exemple de fichier de configuration de stratégie d'éditeur :

```xml
<configuration>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">

            <dependentAssembly>
                <assemblyIdentity name="asm6" publicKeyToken="c0305c36380ba429" />
                <bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0"/>
            </dependentAssembly>

        </assemblyBinding>
    </runtime>
</configuration>
```

Pour créer un assembly, utilisez l’outil [Al.exe (Assembly Linker)](../tools/al-exe-assembly-linker.md) avec une commande telle que la suivante :

```console
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0
```

`compatkey.dat` est un fichier de clé de nom fort. Cette commande crée un assembly de nom fort que vous pouvez placer dans le Global Assembly Cache.

> [!NOTE]
> La stratégie d'éditeur est appliquée à toutes les applications qui utilisent un composant partagé.

Le fichier de configuration de la stratégie d'éditeur substitue les informations de version fournies par l'application (c'est-à-dire celles du manifeste de l'assembly ou du fichier de configuration de l'application). Si aucune instruction dans le fichier de configuration de l'application ne redirige la version qui est spécifiée dans le manifeste de l'assembly, le fichier de stratégie d'éditeur substitue cette version. En revanche, si une instruction de redirection est indiquée dans le fichier de configuration de l'application, le fichier de stratégie d'éditeur substitue cette version et non celle qui est spécifiée dans le manifeste.

Un fichier de stratégie d'éditeur est utilisé quand un composant partagé est mis à jour et que la nouvelle version de ce composant doit être utilisée par toutes les applications partageant le composant. Les paramètres définis dans le fichier de stratégie d'éditeur substituent ceux du fichier de configuration de l'application, sauf si ce dernier applique le mode sans échec.

#### <a name="safe-mode"></a>Mode sans échec

Les fichiers de stratégie d'éditeur sont généralement installés explicitement avec un Service Pack ou une mise à jour de programme. En cas de problème avec le composant partagé mis à jour, vous pouvez ignorer les substitutions spécifiées dans le fichier de stratégie d'éditeur en utilisant le mode sans échec. Le mode sans échec est déterminé par l' **\<publisherPolicy apply="yes**&#124;**no"/>** élément, situé uniquement dans le fichier de configuration de l’application. Il spécifie si les informations de configuration du fichier de stratégie d'éditeur doivent être supprimées du processus de liaison.

Le mode sans échec peut être défini pour toute l'application ou pour des assemblys spécifiques. Autrement dit, vous pouvez désactiver la stratégie pour tous les assemblys qui composent votre application ou l'activer pour certains assemblys seulement. Pour appliquer de manière sélective une stratégie d’éditeur aux assemblys qui composent une application, définissez **\<publisherPolicy apply\=no/>** et spécifiez les assemblys que vous souhaitez affecter à l’aide de l' \<**dependentAssembly**> élément. Pour appliquer la stratégie d’éditeur à tous les assemblys qui composent l’application, définissez sans **\<publisherPolicy apply\=no/>** éléments d’assembly dépendants. Pour plus d'informations sur la configuration, consultez [Configuration des applications à l'aide de fichiers de configuration](../configure-apps/index.md).

### <a name="machine-configuration-file"></a>Fichier de configuration de l'ordinateur

Finalement, le runtime examine le fichier de configuration de l'ordinateur. Ce fichier, intitulé Machine.config, réside sur l'ordinateur local dans le sous-répertoire Config du répertoire racine où le runtime est installé. Il peut être utilisé par les administrateurs pour spécifier des restrictions de liaison d'assemblys qui sont propres à cet ordinateur. Les paramètres définis dans le fichier de configuration de l'ordinateur sont prioritaires par rapport aux autres paramètres de configuration. Cependant, cela ne signifie pas que tous les paramètres de configuration doivent être placés dans ce fichier. La version déterminée par le fichier de stratégie d'administrateur est finale et ne peut pas être substituée. Les substitutions spécifiées dans le fichier Machine.config s'appliquent à toutes les applications. Pour plus d'informations sur les fichiers de configuration, consultez [Configuration des applications à l'aide de fichiers de configuration](../configure-apps/index.md).

<a name="step2"></a>

## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Étape 2 : recherche des assemblys précédemment référencés

Si l'assembly demandé a aussi été demandé lors d'appels précédents, le common language runtime utilise l'assembly qui est déjà chargé. Ceci peut avoir des implications au moment de l'attribution des noms des assemblys qui composent une application. Pour plus d'informations sur l'attribution des noms des assemblys, voir [Noms d'assemblys](../../standard/assembly/names.md).

Si une précédente demande de chargement de l'assembly avait échoué, toute nouvelle demande échoue immédiatement sans qu'aucune tentative de chargement de l'assembly ne soit effectuée. Depuis la version 2.0 du .NET Framework, les échecs de liaison d'assemblys sont mis en cache et les informations mises en cache sont utilisées pour déterminer s'il faut essayer de charger l'assembly.

> [!NOTE]
> Pour rétablir le comportement des versions 1,0 et 1,1 du .NET Framework, qui n’ont pas mis en cache les échecs de liaison, incluez l' [ \<disableCachingBindingFailures> élément](../configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) dans votre fichier de configuration.

<a name="step3"></a>

## <a name="step-3-checking-the-global-assembly-cache"></a>Étape 3 : vérification du Global Assembly Cache

Pour les assemblys avec un nom fort, le processus de liaison examine ensuite le Global Assembly Cache. Le Global Assembly Cache stocke des assemblys qui peuvent être utilisés par plusieurs applications sur un ordinateur. Tous les assemblys figurant dans le Global Assembly Cache doivent avoir un nom fort.

<a name="step4"></a>

## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Étape 4 : localisation de l'assembly par le biais des bases de code ou de la détection

Une fois que la version correcte de l'assembly a été déterminée d'après les informations contenues dans la référence de l'assembly appelant et dans les fichiers de configuration, et après la vérification du Global Assembly Cache (uniquement pour les assemblys avec un nom fort), le common language runtime tente de trouver l'assembly. Le processus de localisation d'un assembly implique les étapes suivantes :

1. Si un [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément est trouvé dans le fichier de configuration de l’application, le runtime vérifie l’emplacement spécifié. Si une correspondance est trouvée, cet assembly est utilisé et aucune détection n'est effectuée. Si l'assembly ne se trouve pas dans cet emplacement, la demande de liaison échoue.

2. Le runtime tente ensuite de détecter l'assembly référencé en utilisant les règles spécifiées plus loin dans cette section.

> [!NOTE]
> Si vous disposez de plusieurs versions d’un assembly dans un répertoire et que vous souhaitez référencer une version particulière de cet assembly, vous devez utiliser l' [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément au lieu de l' `privatePath` attribut de l' [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) élément. Si vous utilisez l' [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) élément, le runtime arrête la détection la première fois qu’il trouve un assembly qui correspond au nom d’assembly simple référencé, qu’il s’agisse d’une correspondance correcte ou non. Si la correspondance est correcte, cet assembly est utilisé. Si elle ne l'est pas, la détection s'interrompt et la liaison échoue.

### <a name="locating-the-assembly-through-codebases"></a>Localisation de l'assembly par bases de code

Les informations de code base peuvent être fournies à l’aide d’un [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément dans un fichier de configuration. Cette base de code est toujours vérifiée avant que le runtime ne tente de détecter l'assembly référencé. Si un fichier de stratégie d’éditeur contenant la redirection de version finale contient également un [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément, cet [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément est celui qui est utilisé. Par exemple, si votre fichier de configuration de l’application spécifie un [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément et qu’un fichier de stratégie d’éditeur qui substitue les informations de l’application spécifie également un [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément, l' [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément dans le fichier de stratégie d’éditeur est utilisé.

Si aucune correspondance n’est trouvée à l’emplacement spécifié par l' [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément, la demande de liaison échoue et aucune autre étape n’est prise. Si le runtime détermine qu'un assembly correspond au critère de l'assembly appelant, il utilise cet assembly. Lorsque le fichier spécifié par l' [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément donné est chargé, le runtime vérifie que le nom, la version, la culture et la clé publique correspondent bien à la référence de l’assembly appelant.

> [!NOTE]
> Les assemblys référencés en dehors du répertoire racine de l’application doivent avoir un nom fort et doivent être installés dans le Global Assembly Cache ou spécifiés à l’aide de l' [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) élément.

### <a name="locating-the-assembly-through-probing"></a>Localisation de l'assembly par détection

S’il n’y a pas [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) d’élément dans le fichier de configuration de l’application, le runtime détecte l’assembly à l’aide de quatre critères :

- La base de l'application, qui est l'emplacement racine où l'application s'exécute.

- La culture, qui est l'attribut de culture de l'assembly référencé.

- Le nom, qui est le nom de l'assembly référencé.

- L' `privatePath` attribut de l' [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) élément, qui est la liste définie par l’utilisateur des sous-répertoires sous l’emplacement racine. Cet emplacement peut être spécifié dans le fichier de configuration de l'application et dans le code managé en utilisant la propriété <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> pour un domaine d'application. Quand il est spécifié dans le code managé, l'attribut `privatePath` du code managé est détecté en premier, suivi du chemin d'accès spécifié dans le fichier de configuration de l'application.

#### <a name="probing-the-application-base-and-culture-directories"></a>Détection de la base de l'application et des répertoires de culture

Le runtime commence toujours le processus de détection dans la base de l'application, qui peut être une URL ou le répertoire racine de l'application sur un ordinateur. Si l'assembly référencé n'est pas trouvé dans la base de l'application et qu'aucune information de culture n'est fournie, le runtime recherche des sous-répertoires avec le nom de l'assembly. Les répertoires détectés sont les suivants :

- [base de l'application] / [nom de l'assembly].dll

- [base de l'application] / [nom de l'assembly] / [nom de l'assembly].dll

Si les informations de culture sont spécifiées pour l'assembly référencé, seuls les répertoires suivants sont détectés :

- [base de l'application] / [culture] / [nom de l'assembly].dll

- [base de l'application] / [culture] / [nom de l'assembly] / [nom de l'assembly].dll

#### <a name="probing-with-the-privatepath-attribute"></a>Détection avec l'attribut privatePath

En plus des sous-répertoires de culture et des sous-répertoires nommés pour l’assembly référencé, le runtime sonde également les répertoires spécifiés à l’aide `privatePath` de l’attribut de l' [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) élément. Les répertoires spécifiés avec l'attribut `privatePath` doivent être des sous-répertoires du répertoire racine de l'application. Les répertoires détectés varient en fonction de la présence d'informations de culture dans la demande de l'assembly référencé.

Le runtime interrompt la détection dès qu'il trouve le premier assembly correspondant au nom simple d'assembly référencé, que cette correspondance soit correcte ou non. Si la correspondance est correcte, cet assembly est utilisé. Si elle ne l'est pas, la détection s'interrompt et la liaison échoue.

Si des informations de culture sont incluses, les répertoires suivants sont détectés :

- [base de l'application] / [chemin bin] / [culture] / [nom de l'assembly].dll

- [base de l'application] / [chemin bin] / [culture] / [nom de l'assembly] / [nom de l'assembly].dll

Si des informations de culture ne sont pas incluses, les répertoires suivants sont détectés :

- [base de l'application] / [chemin bin] / [nom de l'assembly].dll

- [base de l'application] / [chemin bin] / [nom de l'assembly] / [nom de l'assembly].dll

#### <a name="probing-examples"></a>Exemples de détection

Les exemples donnés sont basés sur les informations suivantes :

- Nom de l'assembly référencé : myAssembly

- Répertoire racine de l’application : `http://www.code.microsoft.com`

- [\<probing>](../configure-apps/file-schema/runtime/probing-element.md) l’élément dans le fichier de configuration spécifie : bin

- Culture : de

Le runtime détecte les URL suivantes :

- `http://www.code.microsoft.com/de/myAssembly.dll`

- `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`

##### <a name="multiple-assemblies-with-the-same-name"></a>Plusieurs assemblys ayant le même nom

L'exemple suivant indique comment configurer plusieurs assemblys ayant le même nom.

```xml
<dependentAssembly>
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />
   <codeBase version="1.0.0.0" href="v1/Server.dll" />
   <codeBase version="2.0.0.0" href="v2/Server.dll" />
</dependentAssembly>
```

#### <a name="other-locations-probed"></a>Autres emplacements détectés

L'emplacement de l'assembly peut aussi être déterminé d'après le contexte de liaison actuel. Cela se produit le plus souvent quand la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> est utilisée dans des scénarios COM Interop. Si un assembly utilise la méthode <xref:System.Reflection.Assembly.LoadFrom%2A> pour référencer un autre assembly, l'emplacement de l'assembly appelant est considéré comme étant une indication de l'emplacement de l'assembly référencé. Si une correspondance est trouvée, cet assembly est chargé. Si aucune correspondance n'est trouvée, le runtime continue ses recherches sémantiques, puis demande à Windows Installer de lui fournir l'assembly. Si aucun assembly correspondant à la demande de liaison n'est fourni, une exception est levée. Il s'agit d'une exception <xref:System.TypeLoadException> dans le code managé si un type a été référencé ou d'une exception <xref:System.IO.FileNotFoundException> si un assembly à charger n'a pas été trouvé.

Par exemple, si Assembly1 référence Assembly2 et qu’Assembly1 a été chargé à partir de `http://www.code.microsoft.com/utils`, cet emplacement est considéré comme étant une indication de l’emplacement d’Assembly2.dll. Le runtime sonde alors l’assembly dans `http://www.code.microsoft.com/utils/Assembly2.dll` et `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`. Si Assembly2 n'est pas trouvé dans ces emplacements, le runtime demande à Windows Installer de lui fournir l'assembly.

## <a name="see-also"></a>Voir aussi

- [Meilleures pratiques pour le chargement d'assembly](best-practices-for-assembly-loading.md)
- [Déploiement](index.md)
