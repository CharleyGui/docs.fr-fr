---
title: Création d'assemblys satellites pour les applications bureautiques
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
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5ad89e24bfc55497af52b827717b8b3965bd600
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041006"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Création d'assemblys satellites pour les applications bureautiques

Les fichiers de ressources jouent un rôle central dans les applications localisées. Ils permettent à une application d’afficher des chaînes, des images et d’autres données dans la langue et la culture de l’utilisateur, et de fournir des données de remplacement si les ressources relatives à la langue et la culture de l’utilisateur ne sont pas disponibles. Le .NET Framework utilise un modèle Hub and Spoke pour localiser et récupérer les ressources localisées. Le hub est l’assembly principal qui contient le code exécutable non localisable et les ressources pour une culture unique, appelée culture neutre ou par défaut. La culture par défaut est la culture de secours de l’application ; elle est utilisée quand aucune ressource localisée n’est disponible. Vous utilisez l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour désigner la culture de la culture par défaut de l’application. Chaque spoke se connecte à un assembly satellite qui contient les ressources d’une culture localisée unique, mais ne contient pas de code. Dans la mesure où les assemblys satellites ne font pas partie de l’assembly principal, vous pouvez facilement remplacer ou mettre à jour les ressources correspondant à une culture spécifique sans remplacer l’assembly principal de l’application.

> [!NOTE]
> Les ressources de la culture par défaut d’une application peuvent aussi être stockées dans un assembly satellite. Pour cela, vous affectez à l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> la valeur <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.

## <a name="satellite-assembly-name-and-location"></a>Nom et emplacement de l’assembly satellite

Le modèle Hub and Spoke nécessite que vous placiez les ressources à des emplacements spécifiques afin qu’elles soient facilement trouvées et utilisées. Si vous ne compilez pas et ne nommez pas les ressources comme prévu ou si vous ne les placez pas aux endroits corrects, le Common Language Runtime ne sera pas en mesure de les trouver et utilisera les ressources de la culture par défaut à la place. Le gestionnaire des ressources du .NET Framework, représenté par un objet <xref:System.Resources.ResourceManager>, permet d’accéder automatiquement aux ressources localisées. Le gestionnaire des ressources nécessite les éléments suivants :

- Un seul assembly satellite doit inclure toutes les ressources d’une culture particulière. En d’autres termes, vous devez compiler plusieurs fichiers .txt ou .resx en un seul fichier .resources binaire.

- Il doit exister un sous-répertoire distinct dans le répertoire de l’application pour chaque culture localisée qui stocke les ressources de cette culture. Le nom du sous-répertoire doit être identique au nom de la culture. Vous pouvez aussi stocker vos assemblys satellites dans le Global Assembly Cache. Dans ce cas, le composant des informations de culture du nom fort de l’assembly doit indiquer sa culture. (Consultez la section [Installation d’assemblys satellites dans le Global Assembly Cache](#SN) plus loin dans cette rubrique.)

  > [!NOTE]
  > Si votre application comporte des ressources pour les sous-cultures, placez chaque sous-culture dans un sous-répertoire distinct sous le répertoire de l’application. Ne placez pas les sous-cultures dans des sous-répertoires sous le répertoire de leur culture principale.

- L’assembly satellite doit avoir le même nom que l’application et doit utiliser l’extension de nom de fichier « . resources.dll ». Par exemple, si une application est nommée Example.exe, le nom de chaque assembly satellite doit être Example.resources.dll. Notez que le nom de l’assembly satellite n’indique pas la culture de ses fichiers de ressources. Toutefois, l’assembly satellite apparaît dans un répertoire qui spécifie la culture.

- Des informations sur la culture de l’assembly satellite doivent être incluses dans les métadonnées de l’assembly. Pour stocker le nom de culture dans les métadonnées de l’assembly satellite, vous spécifiez l’option `/culture` quand vous utilisez [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) pour incorporer des ressources dans l’assembly satellite.

L’illustration suivante propose un exemple de structure de répertoires et de la configuration requise pour les emplacements des applications que vous n’installez pas dans le [Global Assembly Cache](../../../docs/framework/app-domains/gac.md). Les éléments avec les extensions .txt et .resources ne sont pas fournis avec l’application finale. Il s’agit des fichiers de ressources intermédiaires utilisés pour créer les assemblys de ressources satellites finaux. Dans cet exemple, vous pouvez remplacer les fichiers .txt par les fichiers .resx. Pour plus d’informations, consultez [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

L’illustration suivante montre le répertoire d’assemblys satellites :

![Répertoire d’assemblys satellites avec sous-répertoires de cultures localisées.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a>compiler des assemblys satellites

Vous utilisez le [Générateur de fichiers de ressources (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour compiler les fichiers texte ou XML (.resx) qui contiennent des ressources en fichiers .resources binaires. Vous utilisez ensuite [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour compiler les fichiers .resources en assemblys satellites. Al.exe crée un assembly à partir des fichiers .resources que vous spécifiez. Les assemblys satellites ne peuvent contenir que des ressources ; ils ne peuvent contenir aucun code exécutable.

La commande Al.exe suivante crée un assembly satellite pour l’application `Example` à partir du fichier de ressources en allemand strings.de.resources.

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

La commande Al.exe suivante crée également un assembly satellite pour l’application `Example` à partir du fichier strings.de.resources. L’option **/template** permet à l’assembly satellite d’hériter de toutes les métadonnées de l’assembly à l’exception des informations de culture de l’assembly parent (Example.dll).

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```

Le tableau suivant décrit plus en détail les options Al.exe utilisées dans ces commandes.

|Option|Description|
|------------|-----------------|
|**-target:** lib|Spécifie que votre assembly satellite est compilé dans un fichier de bibliothèque (.dll). Comme un assembly satellite ne contient pas de code exécutable et n’est pas l’assembly principal d’une application, vous devez enregistrer les assemblys satellites en tant que DLL.|
|**-embed:** strings.de.resources|Spécifie le nom du fichier de ressources à incorporer quand Al.exe compile l’assembly. Vous pouvez incorporer plusieurs fichiers .resources dans un assembly satellite mais, si vous suivez le modèle Hub and Spoke, vous devez compiler un assembly satellite pour chaque culture. Toutefois, vous pouvez créer des fichiers .resources séparés pour les chaînes et les objets.|
|**-culture:** de|Spécifie la culture de la ressource à compiler. Le Common Language Runtime utilise ces informations lors de la recherche des ressources pour une culture spécifiée. Si vous omettez cette option, Al.exe compile quand même la ressource, mais le runtime n’est pas en mesure de la trouver quand un utilisateur la demande.|
|**-out:** Example.resources.dll|Spécifie le nom du fichier de sortie. Le nom doit respecter la norme d’appellation *baseName*.resources. *extension*, où *baseName* est le nom de l’assembly principal et *extension* est une extension valide (par exemple, .dll). Notez que le runtime n’est pas en mesure de déterminer la culture d’un assembly satellite en fonction du nom de son fichier de sortie ; vous devez utiliser l’option **/culture** pour la spécifier.|
|**-template:** Example.dll|Spécifie un assembly à partir duquel l’assembly satellite va hériter de toutes les métadonnées de l’assembly, à l’exception du champ de culture. Cette option affecte les assemblys satellites uniquement si vous spécifiez un assembly qui a un [nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md).|

Pour obtenir une liste complète des options disponibles avec Al.exe, consultez [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).

## <a name="satellite-assemblies-an-example"></a>Assemblys satellites : Exemple

Voici un exemple « Hello world » simple qui affiche une boîte de message contenant un message d’accueil localisé. L’exemple contient des ressources pour les cultures Anglais (États-Unis), Français (France) et Russe (Russie), et sa culture de secours est Anglais. Pour créer l’exemple, effectuez les étapes suivantes :

1. Créez un fichier de ressources nommé Greeting.resx ou Greeting.txt pour contenir la ressource de la culture par défaut. Stockez une chaîne unique nommée `HelloString` dont la valeur est « Hello world! » dans ce fichier.

2. Pour indiquer que l’anglais (en) est la culture par défaut de l’application, ajoutez l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> suivant au fichier AssemblyInfo de l’application ou au fichier de code source principal qui sera compilé dans l’assembly principal de l’application.

    [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]

3. Ajoutez la prise en charge de cultures supplémentaires (en-US, fr-FR et ru-RU) à l’application comme suit :

    - Pour prendre en charge la culture « en-US » ou Anglais (États-Unis), créez un fichier de ressources nommé Greeting.en-US.resx ou Greeting.en-US.txt et stockez-le dans une chaîne unique nommée `HelloString` dont la valeur est « Hi world! ».

    - Pour prendre en charge la culture « fr-FR » ou Français (France), créez un fichier de ressources nommé Greeting.fr-FR.resx ou Greeting.fr-FR.txt et stockez-le dans une chaîne unique nommée `HelloString` dont la valeur est « Salut tout le monde ! ».

    - Pour prendre en charge la culture « ru-RU » ou Russe (Russie), créez un fichier de ressources nommé Greeting.ru-RU.resx ou Greeting.ru-RU.txt et stockez-le dans une chaîne unique nommée `HelloString` dont la valeur est « Всем привет! ».

4. Utilisez [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour compiler chaque fichier de ressources texte ou XML en un fichier .resources binaire. La sortie est un ensemble de fichiers ayant le même nom de fichier racine que les fichiers .resx ou .txt, mais avec l’extension .resources. Si vous créez l’exemple avec Visual Studio, le processus de compilation est géré automatiquement. Si vous n’utilisez pas Visual Studio, exécutez les commandes suivantes pour compiler les fichiers .resx en fichiers .resources :

    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    Si vos ressources se trouvent dans des fichiers texte au lieu de fichiers XML, remplacez l’extension .resx par .txt.

5. Compilez le code source suivant avec les ressources de la culture par défaut dans l’assembly principal de l’application :

    > [!IMPORTANT]
    > Si vous utilisez la ligne de commande plutôt que Visual Studio pour créer l’exemple, vous devez modifier l’appel au constructeur de la classe <xref:System.Resources.ResourceManager> comme suit :`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`

    [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    Si l’application se nomme Example et que vous compilez à partir de la ligne de commande, la commande pour le compilateur C# est :

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    La commande correspondante du compilateur Visual Basic est :

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. Créez un sous-répertoire dans le répertoire principal de l’application pour chaque culture localisée prise en charge par l’application. Vous devez créer des sous-répertoires en-US, fr-FR et ru-RU. Visual Studio crée automatiquement ces sous-répertoires dans le cadre du processus de compilation.

7. Incorporez les fichiers .resources individuels spécifiques à la culture dans des assemblys satellites et enregistrez-les dans le répertoire approprié. La commande à exécuter pour chaque fichier .resources est la suivante :

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

    où *culture* est le nom de la culture dont les ressources sont contenues dans l’assembly satellite. Visual Studio gère automatiquement ce processus.

Vous pouvez ensuite exécuter l’exemple. Il choisit au hasard comme culture actuelle l’une des cultures prises en charge et affiche un message d’accueil localisé.

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Installation d’assemblys satellites dans le Global Assembly Cache

Au lieu d’installer des assemblys dans un sous-répertoire de l’application locale, vous pouvez les installer dans le Global Assembly Cache. Ceci est particulièrement utile si vous avez des bibliothèques de classes et des assemblys de ressources de bibliothèques de classes qui sont utilisés par plusieurs applications.

Pour être installés dans le Global Assembly Cache, les assemblys doivent avoir un nom fort. Les assemblys avec nom fort sont signés avec une paire de clés publique/privée valide. Ils contiennent des informations de version que le runtime utilise pour déterminer l’assembly à utiliser pour répondre à une demande de liaison. Pour plus d’informations sur les noms forts et le contrôle de version, consultez [Contrôle de version des assemblys](../../../docs/framework/app-domains/assembly-versioning.md). Pour plus d’informations sur les noms forts, consultez [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md).

Quand vous développez une application, il est peu probable que vous puissiez accéder à la paire de clés publique/privée finale. Pour installer un assembly satellite dans le Global Assembly Cache et vous assurer qu’il fonctionne comme prévu, vous pouvez utiliser une technique appelée signature différée. Quand vous différez la signature d’un assembly, vous réservez au moment de la génération un espace dans le fichier pour la signature de nom fort. La signature réelle est différée jusqu’à une date ultérieure, quand la paire de clés publique/privée finale est disponible. Pour plus d’informations sur la signature différée, consultez [Différer la signature d’un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).

### <a name="obtaining-the-public-key"></a>Obtention de la clé publique

Pour différer la signature d’un assembly, vous devez avoir accès à la clé publique. Vous pouvez soit obtenir la clé publique réelle à partir de l’organisation de votre société qui effectuera la signature finale, soit créer une clé publique en utilisant l’outil [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).

La commande Sn.exe suivante crée une paire de clés publique/privée de test. L’option **–k** spécifie que Sn.exe doit créer une paire de clés et l’enregistrer dans un fichier nommé TestKeyPair.snk.

```console
sn –k TestKeyPair.snk
```

Vous pouvez extraire la clé publique du fichier contenant la paire de clés de test. La commande suivante extrait la clé publique de TestKeyPair.snk et l’enregistre dans PublicKey.snk :

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a>Temporisation de signature d'un assembly

Après avoir obtenu ou créé la clé publique, utilisez [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour compiler l’assembly et spécifier une signature différée.

La commande Al.exe suivante crée un assembly satellite avec nom fort pour l’application StringLibrary à partir du fichier strings.ja.resources :

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

L’option **-delay+** indique qu’Assembly Linker doit différer la signature de l’assembly. L’option **-keyfile** spécifie le nom du fichier de clé qui contient la clé publique à utiliser pour différer la signature de l’assembly.

### <a name="re-signing-an-assembly"></a>Nouvelle signature d’un assembly

Avant de déployer votre application, vous devez signer à nouveau l’assembly satellite à signature différée avec la vraie valeur de paire de clés. Pour cela, utilisez Sn.exe.

La commande Sn.exe suivante signe StringLibrary.resources.dll avec la paire de clés stockée dans le fichier RealKeyPair.snk. L’option **–R** spécifie qu’un assembly déjà signé ou à signature différée doit être à nouveau signé.

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Installation d’un assembly satellite dans le Global Assembly Cache

Quand le runtime recherche des ressources dans le processus de secours pour les ressources, il cherche d’abord dans le [Global Assembly Cache](../../../docs/framework/app-domains/gac.md). (Pour plus d’informations, consultez la section « Processus de secours pour les ressources » de la rubrique [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).) Dès qu’un assembly satellite est signé avec un nom fort, il peut être installé dans le Global Assembly Cache à l’aide de [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).

La commande Gacutil.exe suivante installe StringLibrary.resources.dll dans le Global Assembly Cache :

```console
gacutil -i:StringLibrary.resources.dll
```

L’option **/i** spécifie que Gacutil.exe doit installer l’assembly spécifié dans le Global Assembly Cache. Une fois l’assembly satellite installé dans le cache, les ressources qu’il contient deviennent disponibles pour toutes les applications conçues pour utiliser l’assembly satellite.

### <a name="resources-in-the-global-assembly-cache-an-example"></a>Ressources dans le Global Assembly Cache : Exemple

L’exemple suivant utilise une méthode dans une bibliothèque de classes .NET Framework pour extraire et retourner un message d’accueil localisé à partir d’un fichier de ressources. La bibliothèque et ses ressources sont inscrites dans le Global Assembly Cache. L’exemple contient des ressources pour les cultures Anglais (États-Unis), Français (France) et Russe (Russie). L’anglais est la culture par défaut ; ses ressources sont stockées dans l’assembly principal. L’exemple diffère initialement la signature de la bibliothèque et ses assemblys satellites avec une clé publique, puis les signe à nouveau avec une paire de clés publique/privée. Pour créer l’exemple, effectuez les étapes suivantes :

1. Si vous n’utilisez pas Visual Studio, utilisez la commande [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) suivante pour créer une paire de clés publique/privée nommée ResKey.snk :

    ```console
    sn –k ResKey.snk
    ```

    Si vous utilisez Visual Studio, utilisez l’onglet **Signature** de la boîte de dialogue **Propriétés** du projet pour générer le fichier de clé.

2. Utilisez la commande [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) suivante pour créer un fichier de clé publique nommé PublicKey.snk :

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. Créez un fichier de ressources nommé Strings.resx pour contenir la ressource de la culture par défaut. Stockez une chaîne unique nommée `Greeting` dont la valeur est « How do you do? » dans ce fichier.

4. Pour indiquer que l’anglais « en » est la culture par défaut de l’application, ajoutez l’attribut <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> suivant au fichier AssemblyInfo de l’application ou au fichier de code source principal qui sera compilé dans l’assembly principal de l’application :

    [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. Ajoutez la prise en charge de cultures supplémentaires (en-US, fr-FR et ru-RU) à l’application comme suit :

    - Pour prendre en charge la culture « en-US » ou Anglais (États-Unis), créez un fichier de ressources nommé Strings.en-US.resx ou Strings.en-US.txt et stockez-le dans une chaîne unique nommée `Greeting` dont la valeur est « Hello! ».

    - Pour prendre en charge la culture « fr-FR » ou Français (France), créez un fichier de ressources nommé Strings.fr-FR.resx ou Strings.fr-FR.txt et stockez-le dans une chaîne unique nommée `Greeting` dont la valeur est « Bonjour ! ».

    - Pour prendre en charge la culture « ru-RU » ou Russe (Russie), créez un fichier de ressources nommé Strings.ru-RU.resx ou Strings.ru-RU.txt et stockez-le dans une chaîne unique nommée `Greeting` dont la valeur est « Привет! ».

6. Utilisez [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour compiler chaque fichier de ressources texte ou XML en un fichier .resources binaire. La sortie est un ensemble de fichiers ayant le même nom de fichier racine que les fichiers .resx ou .txt, mais avec l’extension .resources. Si vous créez l’exemple avec Visual Studio, le processus de compilation est géré automatiquement. Si vous n’utilisez pas Visual Studio, exécutez la commande suivante pour compiler les fichiers .resx en fichiers .resources :

    ```console
    resgen filename
    ```

    où *filename* représente le chemin d’accès facultatif, le nom de fichier et l’extension du fichier .resx ou texte.

7. Compilez le code source suivant pour StringLibrary.vb ou StringLibrary.cs avec les ressources de la culture par défaut dans un assembly de bibliothèque à signature différée nommé StringLibrary.dll :

    > [!IMPORTANT]
    > Si vous utilisez la ligne de commande plutôt que Visual Studio pour créer l’exemple, vous devez remplacer l’appel au constructeur de la classe <xref:System.Resources.ResourceManager> par `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.

    [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    La commande pour le compilateur C# est :

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    La commande correspondante du compilateur Visual Basic est :

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. Créez un sous-répertoire dans le répertoire principal de l’application pour chaque culture localisée prise en charge par l’application. Vous devez créer des sous-répertoires en-US, fr-FR et ru-RU. Visual Studio crée automatiquement ces sous-répertoires dans le cadre du processus de compilation. Comme tous les assemblys satellites ont le même nom de fichier, les sous-répertoires permettent de stocker des assemblys satellites individuels spécifiques à la culture jusqu’à ce qu’ils soient signés avec une paire de clés publique/privée.

9. Incorporez les fichiers .resources individuels spécifiques à la culture dans des assemblys satellites à signature différée et enregistrez-les dans le répertoire approprié. La commande à exécuter pour chaque fichier .resources est la suivante :

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    où *culture* est le nom d’une culture. Dans cet exemple, les noms de culture sont en-US, fr-FR et ru-RU.

10. Signez à nouveau StringLibrary.dll à l’aide de [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) comme suit :

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. Signez à nouveau les assemblys satellites individuels. Pour ce faire, utilisez [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) comme suit pour chaque assembly satellite :

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. Inscrivez StringLibrary.dll et chacun de ses assemblys satellites dans le Global Assembly Cache à l’aide de la commande suivante :

    ```console
    gacutil -i filename
    ```

    où *filename* représente le nom du fichier à inscrire.

13. Si vous utilisez Visual Studio, créez un projet **Application console** nommé `Example`, ajoutez-lui une référence à StringLibrary.dll et le code source suivant, puis compilez.

    [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    Pour compiler à partir de la ligne de commande, utilisez la commande suivante pour le compilateur C# :

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    La ligne de commande pour le compilateur Visual Basic est :

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. Exécutez Example.exe.

## <a name="see-also"></a>Voir aussi

- [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Temporisation de signature d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (outil Strong Name)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (outil Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
- [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)
