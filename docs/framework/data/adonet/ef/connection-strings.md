---
title: Chaînes de connexion dans le Entity Framework ADO.NET
description: En savoir plus sur les chaînes de connexion dans le Entity Framework, qui contiennent des informations pour se connecter au fournisseur de données ADO.NET et à propos des fichiers de modèle et de mappage.
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 2ae25f5881c033a84d65f5b0b4ed14b4866dbcb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286868"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>Chaînes de connexion dans le Entity Framework ADO.NET

Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données. La syntaxe dépend du fournisseur de données et la chaîne de connexion est analysée lors de la tentative d'ouverture d'une connexion. Les chaînes de connexion utilisées par Entity Framework contiennent des informations utilisées pour la connexion au fournisseur de données ADO.NET sous-jacent qui prend en charge Entity Framework. Elles contiennent également des informations sur les fichiers de modèle et de mappage requis.

La chaîne de connexion est utilisée par le fournisseur EntityClient lors de l'accès aux métadonnées de modèle et de mappage et de la connexion à la source de données. Il est possible d'accéder à cette chaîne ou de la définir via la propriété <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> de <xref:System.Data.EntityClient.EntityConnection>. La classe <xref:System.Data.EntityClient.EntityConnectionStringBuilder> peut être utilisée pour construire par programme des paramètres dans la chaîne de connexion ou y accéder par programme. Pour plus d’informations, consultez [Comment : générer une chaîne de connexion EntityConnection](how-to-build-an-entityconnection-connection-string.md).

Les [outils de Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) génèrent une chaîne de connexion stockée dans le fichier de configuration de l’application. <xref:System.Data.Objects.ObjectContext> récupère automatiquement ces informations de connexion lors de la création de requêtes d'objet. Il est possible d'accéder au <xref:System.Data.EntityClient.EntityConnection> utilisé par une instance de <xref:System.Data.Objects.ObjectContext> à partir de la propriété <xref:System.Data.Objects.ObjectContext.Connection%2A>. Pour plus d’informations, consultez [gestion des connexions et des transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Syntaxe des chaînes de connexion

Pour en savoir plus sur la syntaxe générale pour les chaînes de connexion, consultez [syntaxe de chaîne de connexion | Chaînes de connexion dans ADO.NET](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Paramètres de chaîne de connexion

Le tableau suivant répertorie les noms valides pour les valeurs de mots clés dans la propriété <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.

|Mot clé|Description|
|-------------|-----------------|
|`Provider`|Obligatoire si le mot clé `Name` n'est pas spécifié. Nom du fournisseur, utilisé pour récupérer l'objet <xref:System.Data.Common.DbProviderFactory> du fournisseur sous-jacent. Cette valeur est constante.<br /><br /> Lorsque le mot clé `Name` n'est pas inclus dans une chaîne de connexion de l'entité, une valeur non vide pour le mot clé `Provider` est requise. Ce mot clé et le mot clé `Name` s'excluent mutuellement.|
|`Provider Connection String`|facultatif. Spécifie la chaîne de connexion spécifique au fournisseur passée à la source de données sous-jacente. Cette chaîne de connexion contient des paires mot clé/valeur valides pour le fournisseur de données. Un mot clé `Provider Connection String` non valide provoque une erreur d'exécution lors de son évaluation par la source de données.<br /><br /> Ce mot clé et le mot clé `Name` s'excluent mutuellement.<br /><br /> Veillez à placer la valeur dans une séquence d’échappement en fonction de la syntaxe générale des [chaînes de connexion ADO.net](../connection-strings.md). Prenons l’exemple de la chaîne de connexion suivante : `Server=serverName; User ID = userID` . Elle doit être placée dans une séquence d’échappement, car elle contient un point-virgule. Étant donné qu’il ne contient pas de guillemets doubles, ils peuvent être utilisés pour l’échappement :<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|Obligatoire si le mot clé `Name` n'est pas spécifié. Liste de répertoires, de fichiers et d'emplacements de ressources délimités par des barres verticales (|) où rechercher les métadonnées et les informations de mappage. Par exemple :<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Les espaces situés de part et d'autre de la barre verticale sont ignorés.<br /><br /> Ce mot clé et le mot clé `Name` s'excluent mutuellement.|
|`Name`|L'application peut éventuellement spécifier le nom de la connexion dans un fichier de configuration d'application qui fournit les valeurs de chaîne de connexion mot clé/valeur requises. Dans ce cas, vous ne pouvez pas les fournir directement dans la chaîne de connexion. Le mot clé `Name` n'est pas autorisé dans un fichier de configuration.<br /><br /> Lorsque le mot clé `Name` n'est pas inclus dans la chaîne de connexion, des valeurs non vides pour le mot clé Provider sont requises.<br /><br /> Ce mot clé est incompatible avec tous les autres mots clés de chaîne de connexion, et inversement.|

Voici un exemple de chaîne de connexion pour le modèle de [vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) stocké dans le fichier de configuration de l’application :

## <a name="model-and-mapping-file-locations"></a>Emplacement des fichiers de modèle et de mappage

Le paramètre `Metadata` contient une liste d'emplacements dans lesquels le fournisseur `EntityClient` va rechercher les fichiers de modèle et de mappage. Les fichiers de modèle et de mappage sont souvent déployés dans le même répertoire que le fichier exécutable de l'application. Ces fichiers peuvent être déployés également dans un emplacement spécifique ou inclus en tant que ressource incorporée dans l'application.

Les ressources incorporées sont spécifiées comme suit :

`Metadata=res://<assemblyFullName>/<resourceName>`

Les options suivantes permettent de définir l'emplacement d'une ressource incorporée :

|Option|Description|
|-|-|
|`assemblyFullName`|Nom complet d'un assembly avec la ressource incorporée. Ce nom inclut le nom simple, le nom de la version, la culture prise en charge et la clé publique, comme suit :<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Il est possible d'incorporer des ressources dans n'importe quel assembly accessible par l'application.<br /><br /> Si vous spécifiez un caractère générique ( \* ) pour `assemblyFullName` , le runtime de Entity Framework recherche les ressources aux emplacements suivants, dans cet ordre :<br /><br /> 1. assembly appelant.<br />2. assemblys référencés.<br />3. les assemblys dans le répertoire bin d’une application.<br /><br /> Si les fichiers ne se trouvent pas dans l'un de ces emplacements, une exception est levée. **Remarque :**  Quand vous utilisez un caractère générique (*), le Entity Framework doit rechercher dans tous les assemblys les ressources portant le nom correct. Pour améliorer les performances, spécifiez le nom de l'assembly plutôt que le caractère générique.|
|`resourceName`|Nom de la ressource incluse, par exemple AdventureWorksModel. csdl. Les services de métadonnées ne recherchent que les fichiers ou les ressources ayant l’une des extensions suivantes : .csdl, .ssdl, or .msl. Si `resourceName` n'est pas spécifié, toutes les ressources de métadonnées sont chargées. Les ressources doivent avoir des noms uniques dans un assembly. Si plusieurs fichiers portant le même nom sont définis dans différents répertoires de l’assembly, l’option `resourceName` doit inclure la structure de dossiers avant le nom de la ressource, par exemple NomDossier.NomFichier.csdl.<br /><br /> `resourceName` n'est pas requis lorsque vous spécifiez un caractère générique (*) pour `assemblyFullName`.|

> [!NOTE]
> Pour améliorer les performances, incorporez les ressources dans l'assembly appelant, excepté dans les scénarios non Web dans lesquels il n'y a aucune référence aux fichiers de mappage et de métadonnées sous-jacents dans l'assembly appelant.

L'exemple suivant charge tous les fichiers de modèle et de mappage de l'assembly appelant, des assemblys référencés et des autres assemblys situés dans le répertoire bin d'une application.

```csharp
Metadata=res://*/
```

L'exemple suivant charge le fichier model.csdl à partir de l'assembly AdventureWorks, et charge les fichiers model.ssdl et model.msl à partir du répertoire par défaut de l'application en cours d'exécution.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

L'exemple suivant charge les trois ressources spécifiées à partir de l'assembly spécifique.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

L'exemple suivant charge toutes les ressources incorporées ayant les extensions .csdl, .msl et .ssdl à partir de l'assembly.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

L’exemple suivant charge toutes les ressources dans le chemin de fichier relatif plus « datadir\metadata \\ » à partir de l’emplacement de l’assembly chargé.

```csharp
Metadata=datadir\metadata\
```

L’exemple suivant charge toutes les ressources se trouvant dans le chemin d’accès relatif à partir de l’emplacement de l’assembly chargé.

```csharp
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Prise en charge de la chaîne de substitution &#124;DataDirectory&#124; et de l’opérateur racine de l’application Web (~)

`DataDirectory`et l’opérateur ~ sont utilisés dans le cadre <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> des `Metadata` `Provider Connection String` Mots clés et. L'objet <xref:System.Data.EntityClient.EntityConnection> transfère le répertoire `DataDirectory` et l'opérateur ~ à l'objet <xref:System.Data.Metadata.Edm.MetadataWorkspace> et au fournisseur de magasins, respectivement.

|Terme|Description|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Correspond à un chemin d’accès relatif aux fichiers de mappage et de métadonnées. Il s'agit de la valeur définie via la méthode `AppDomain.SetData("DataDirectory", objValue)`. La `DataDirectory` chaîne de substitution doit être entourée des caractères de barre verticale et il ne peut pas y avoir d’espace blanc entre son nom et les caractères de barre verticale. Le nom `DataDirectory` ne respecte pas la casse.<br /><br /> Si un répertoire physique nommé « DataDirectory » doit être passé en tant que membre de la liste des chemins d’accès aux métadonnées, ajoutez un espace blanc à l’un ou l’autre des deux côtés du nom. Par exemple : `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Une application ASP.NET résout &#124;&#124; DataDirectory dans le dossier « \<application root> /App_Data ».|
|~|Correspond à la racine de l'application Web. Le caractère ~ placé en première position est toujours interprété comme l'opérateur de racine de l'application Web (~), même s'il peut représenter un sous-répertoire local valide. Pour faire référence à un tel sous-répertoire local, l'utilisateur doit passer explicitement `./~`.|

`DataDirectory` et l'opérateur ~ doivent être spécifiés uniquement au début d'un chemin d'accès ; ils ne sont pas résolus s'ils se trouvent à toute autre position. Entity Framework essaiera de résoudre `~/data`, mais il traitera `/data/~` comme un chemin d'accès physique.

Un chemin d'accès qui commence par le `DataDirectory` ou par l'opérateur ~ ne peut pas correspondre à un chemin d'accès physique à l'extérieur de la branche du `DataDirectory` et de l'opérateur ~. Par exemple, les chemins d’accès suivants seront résolus : `~` , `~/data` , `~/bin/Model/SqlServer`. Les chemins d’accès suivants ne seront pas résolus : `~/..`, `~/../other`.

`DataDirectory` et l'opérateur ~ peuvent être étendus pour inclure des sous-répertoires, comme suit : `|DataDirectory|\Model`, `~/bin/Model`

La résolution de la chaîne de substitution `DataDirectory` et de l’opérateur ~ est non récursive. Par exemple, lorsque `DataDirectory` inclut le caractère `~`, une exception se produit. Cela empêche une récurrence infinie.

## <a name="see-also"></a>Voir aussi

- [Utilisation des fournisseurs de données](working-with-data-providers.md)
- [Considérations relatives au déploiement](deployment-considerations.md)
- [Gestion des connexions et des transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Chaînes de connexion](../connection-strings.md)
