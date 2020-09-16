---
title: EDM Generator (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: da5b87fa76cbc8e44f6ed60b047e5a185c2aa603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542553"
---
# <a name="edm-generator-edmgenexe"></a>EDM Generator (EdmGen.exe)

EdmGen.exe est un outil en ligne de commande utilisé pour travailler avec des fichiers de modèle et de mappage Entity Framework. Vous pouvez utiliser l'outil EdmGen.exe pour effectuer les opérations suivantes :

- Connectez-vous à une source de données à l’aide d’un fournisseur de données .NET Framework spécifique à une source de données et générez les fichiers de modèle conceptuel (. CSDL), de modèle de stockage (. SSDL) et de mappage (. MSL) utilisés par le Entity Framework. Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Valider un modèle existant. Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour valider des fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Générer un fichier de code C# ou Visual Basic qui contient les classes d'objets générées à partir d'un fichier de modèle conceptuel (.csdl). Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer le code de couche objet](how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Générez un fichier de code C# ou Visual Basic qui contient les vues prégénérées d'un modèle existant. Pour plus d’informations, [Comment : prégénérer des vues pour améliorer les performances des requêtes](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

L’outil EdmGen.exe est installé dans le répertoire .NET Framework. Dans de nombreux cas, celui-ci se trouve dans C:\windows\Microsoft.NET\Framework\v4.0. Pour les systèmes 64 bits, il se trouve dans C:\windows\Microsoft.NET\Framework64\v4.0. Vous pouvez également accéder à l’outil EdmGen.exe à partir de l’invite de commandes de Visual Studio (cliquez sur **Démarrer**, pointez sur **tous les programmes**, sur **Microsoft Visual Studio 2010**, sur **Visual Studio Tools**, puis cliquez sur **invite de commandes de Visual Studio 2010**).

## <a name="syntax"></a>Syntaxe

```console
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Mode

Lorsque vous utilisez l'outil EdmGen.exe, vous devez spécifier l'un des modes suivants.

|Mode|Description|
|----------|-----------------|
|`/mode:ValidateArtifacts`|Valide les fichiers .csdl, .ssdl et .msl, et affiche les erreurs ou les avertissements éventuels.<br /><br /> Cette option requiert au moins l'un des arguments `/inssdl` ou `/incsdl`. Si `/inmsl` est spécifié, les arguments `/inssdl` et `/incsdl` sont également requis.|
|`/mode:FullGeneration`|Utilise les informations de connexion à la base de données spécifiées dans l'option `/connectionstring` et génère des fichiers .csdl, .ssdl, .msl, de couche objet et de vue.<br /><br /> Cette option requiert un argument `/connectionstring`, et soit un argument `/project` soit les arguments `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace` et `/entitycontainer`.|
|`/mode:FromSSDLGeneration`|Génère des fichiers .csdl et .msl, du code source et des vues à partir du fichier .ssdl spécifié.<br /><br /> Cette option requiert l’argument `/inssdl`, et soit un argument `/project` soit les arguments `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` et `/entitycontainer`.|
|`/mode:EntityClassGeneration`|Crée un fichier de code source qui contient les classes générées à partir du fichier .csdl.<br /><br /> Cette option requiert l’argument `/incsdl`, et soit l’argument `/project` soit l’argument `/outobjectlayer`. L'argument `/language` est obligatoire.|
|`/mode:ViewGeneration`|Crée un fichier de code source qui contient les vues générées à partir des fichiers .csdl, .ssdl, et .msl.<br /><br /> Cette option requiert les arguments `/inssdl`, `/incsdl`, `/inmsl,` et soit l’argument `/project` soit l’argument `/outviews`. L'argument `/language` est obligatoire.|

## <a name="options"></a>Options

|Option|Description|
|------------|-----------------|
|`/p[roject]:`\<string>|Spécifie le nom de projet à utiliser. Le nom de projet est utilisé comme valeur par défaut pour le paramètre d'espace de noms, le nom du modèle et des fichiers de mappage, le nom du fichier source de l'objet et le nom de fichier source de génération de vues. Le nom du conteneur d’entités est défini sur \<project> Context.|
|`/prov[ider]:`\<string>|Nom du fournisseur de données .NET Framework à utiliser pour générer le fichier de modèle de stockage (.ssdl). Le fournisseur par défaut est le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|`/c[onnectionstring]:`\<connection string>|Spécifie la chaîne utilisée pour se connecter à la source de données.|
|`/incsdl:`\<file>|Spécifie le fichier .csdl ou un répertoire où se trouvent les fichiers .csdl. Cet argument peut être spécifié plusieurs fois afin de pouvoir spécifier plusieurs répertoires ou fichiers .csdl. La spécification de plusieurs répertoires peut être utile pour générer des classes (`/mode:EntityClassGeneration`) ou des vues (`/mode:ViewGeneration`) lorsque le modèle conceptuel est divisé en plusieurs fichiers. Cela peut également être utile lorsque vous voulez valider plusieurs modèles (`/mode:ValidateArtifacts`).|
|`/refcsdl:`\<file>|Spécifie le ou les fichiers .csdl supplémentaires utilisés pour résoudre toute référence dans le fichier .csdl source. (Le fichier .csdl source est le fichier spécifié par l'option `/incsdl`). Le fichier `/refcsdl` contient des types dont dépend le fichier .csdl source. Cet argument peut être spécifié plusieurs fois.|
|`/inmsl:`\<file>|Spécifie le fichier .msl ou un répertoire où se trouvent les fichiers .msl. Cet argument peut être spécifié plusieurs fois afin de pouvoir spécifier plusieurs répertoires ou fichiers .msl. La spécification de plusieurs répertoires peut être utile pour générer des vues (`/mode:ViewGeneration`) lorsque le modèle conceptuel est divisé en plusieurs fichiers. Cela peut également être utile lorsque vous voulez valider plusieurs modèles (`/mode:ValidateArtifacts`).|
|`/inssdl:`\<file>|Spécifie le fichier .ssdl ou un répertoire où se trouvent les fichiers .ssdl. Cet argument peut être spécifié plusieurs fois afin de pouvoir spécifier plusieurs répertoires ou fichiers .ssdl. Cela peut être utile lorsque vous voulez valider plusieurs modèles `(/mode:ValidateArtifacts)`.|
|`/outcsdl:`\<file>|Spécifie le nom du fichier .csdl qui sera créé.|
|`/outmsl:`\<file>|Spécifie le nom du fichier .msl qui sera créé.|
|`/outssdl:`\<file>|Spécifie le nom du fichier .ssdl qui sera créé.|
|`/outobjectlayer:`\<file>|Spécifie le nom du fichier de code source qui contient les objets générés à partir du fichier .csdl.|
|`/outviews:`\<file>|Spécifie le nom du fichier de code source qui contient les vues qui ont été générés.|
|`/language:`[VB&#124;CSharp]|Spécifie le langage des fichiers de code source générés. Le langage par défaut est C#.|
|`/namespace:`\<string>|Spécifie l'espace de noms du modèle à utiliser. L'espace de noms est défini dans le fichier .csdl lors de l'exécution de `/mode:FullGeneration` ou de `/mode:FromSSDLGeneration`. L'espace de noms n'est pas utilisé lors de l'exécution de `/mode:EntityClassGeneration`.|
|`/entitycontainer:`\<string>|Spécifie le nom à appliquer à l'élément `<EntityContainer>` dans le modèle et les fichiers de mappage générés.|
|`/pl[uralize]`|Applique aux noms `Entity`, `EntitySet` et `NavigationProperty` dans le modèle conceptuel les règles de la langue anglaise pour les singuliers et les pluriels. Cette option effectuera les actions suivantes :<br /><br /> -Définir tous les `EntityType` noms au singulier.<br />-Définir tous les `EntitySet` noms au pluriel.<br />-Pour chaque `NavigationProperty` qui retourne au plus une entité, définissez le nom au singulier.<br />-Pour chaque `NavigationProperty` qui retourne plusieurs entités, définissez le nom au pluriel.|
|`/SuppressForeignKeyProperties or /nofk`|Empêche que des colonnes de clé étrangère soient exposées comme propriétés scalaires sur les types d'entité dans le modèle conceptuel.|
|`/help` ou `?`|Affiche la syntaxe et les options de commande de l'outil.|
|`/nologo`|Supprime l'affichage du message de copyright.|
|`/targetversion:` \<string>|Version du .NET Framework qui sera utilisée pour compiler le code généré. Les versions prises en charge sont 4 et 4.5. La valeur par défaut est 4.|

## <a name="in-this-section"></a>Dans cette section

[Procédure : Utiliser EdmGen.exe pour générer des fichiers de modèle et des fichiers de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Procédure : Utiliser EdmGen.exe pour générer le code de couche objet](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Procédure : Utiliser EdmGen.exe pour valider les fichiers de modèle et les fichiers de mappage](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Voir aussi

- [Outils de Entity Data Model ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Entity Data Model](../entity-data-model.md)
- [Spécifications CSDL, SSDL et MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
