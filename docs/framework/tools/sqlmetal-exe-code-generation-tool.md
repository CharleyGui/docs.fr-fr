---
title: SqlMetal.exe (outil de génération de code)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 0d12196acab5a50f7dd6fc78e6dccc098cf3e2de
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894606"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (outil de génération de code)
L’outil en ligne de commande SqlMetal génère le code et le mappage du composant [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] du .NET Framework. En appliquant les options qui apparaissent ultérieurement dans cette rubrique, vous pouvez ordonner à SqlMetal d'exécuter plusieurs actions différentes, dont les suivantes :  
  
- À partir d'une base de données, générez le code source et les attributs de mappage ou un fichier de mappage.  
  
- À partir d'une base de données, générez un fichier .dbml (database markup language) intermédiaire à des fins de personnalisation.  
  
- À partir d'un fichier .dbml, générez du code et des attributs de mappage ou un fichier de mappage.  
  
 Cet outil est installé automatiquement avec Visual Studio. Par défaut, ce fichier se trouve à l'emplacement suivant : `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin. Si vous n’installez pas Visual Studio, vous pouvez également obtenir le fichier SQLMetal en téléchargeant le [SDK Windows](https://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
> Les développeurs qui utilisent Visual Studio peuvent également utiliser le Concepteur Objet Relationnel pour générer des classes d'entité. L'approche de ligne de commande est bien adaptée aux bases de données volumineuses. Puisque SqlMetal est un outil de ligne de commande, vous pouvez l'utiliser dans un processus de génération.  
  
 Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d’informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md). À l’invite de commandes, tapez ce qui suit :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Options  
 Pour afficher la liste des options la plus récente, tapez `sqlmetal /?` à partir d’une invite de commandes depuis l’emplacement d’installation.  
  
 **Options de connexion**  
  
|Option|Description|  
|------------|-----------------|  
|**/server:** *\<nom>*|Spécifie le nom du serveur de base de données.|  
|**/database:** *\<nom>*|Spécifie le catalogue de base de données sur le serveur.|  
|**/user:** *\<nom>*|Spécifie l'ID de connexion de l'utilisateur. Valeur par défaut : Utilisez l’authentification Windows.|  
|**/password:** *\<mot_de_passe>*|Spécifie le mot de passe d'ouverture de session. Valeur par défaut : Utilisez l’authentification Windows.|  
|**/conn:** *\<chaîne_connexion>*|Spécifie la chaîne de connexion de base de données. Ne peut pas être utilisée avec les options **/server**, **/database**, **/user**ou **/password** .<br /><br /> N'inclut pas le nom de fichier dans la chaîne de connexion. Ajoutez plutôt le nom de fichier à la ligne de commande comme fichier d'entrée. Par exemple, la ligne suivante spécifie "c:\northwnd.mdf" comme fichier d’entrée : **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"** .|  
|**/timeout:** *\<secondes>*|Spécifie la valeur du délai d'attente lorsque SqlMetal accède à la base de données. Valeur par défaut : 0 (à savoir, aucune limite de temps).|  
  
 **Options d'extraction**  
  
|Option|Description|  
|------------|-----------------|  
|**/views**|Extrait des vues de base de données.|  
|**/functions**|Extrait des fonctions de base de données.|  
|**/sprocs**|Extrait des procédures stockées.|  
  
 **Options de sortie**  
  
|Option|Description|  
|------------|-----------------|  
|**/dbml** *[:file]*|Envoie la sortie au format .dbml. Ne peut pas être utilisée avec l’option **/map** .|  
|**/code** *[:file]*|Envoie la sortie sous la forme de code source. Ne peut pas être utilisée avec l’option **/dbml** .|  
|**/map** *[:file]*|Génère un fichier de mappage XML plutôt que des attributs. Ne peut pas être utilisée avec l’option **/dbml** .|  
  
 **Divers**  
  
|Option|Description|  
|------------|-----------------|  
|**/language:** *\<langage>*|Spécifie le langage du code source.<br /><br /> *\<langage>* valide : vb, csharp.<br /><br /> Valeur par défaut : Dérivé de l’extension du nom du fichier de code.|  
|**/namespace:** *\<nom>*|Spécifie l'espace de noms du code généré. Valeur par défaut : Aucun espace de noms.|  
|**/context:** *\<type>*|Spécifie le nom de la classe du contexte de données. Valeur par défaut : Dérivé du nom de base de données.|  
|**/entitybase:** *\<type>*|Spécifie la classe de base des classes d'entité du code généré. Valeur par défaut : Les entités n’ont pas de classe de base.|  
|**/pluralize**|Pluralise ou singularise automatiquement des noms de membre et de classe.<br /><br /> Cette option est disponible uniquement dans la version Anglais américain.|  
|**/serialization:** *\<option>*|Génère des classes sérialisables.<br /><br /> *\<option>* valide : Aucun, Unidirectionnel. Valeur par défaut : Aucune.<br /><br /> Pour plus d’informations, consultez [Sérialisation](../../../docs/framework/data/adonet/sql/linq/serialization.md).|  
  
 **Fichier d'entrée**  
  
|Option|Description|  
|------------|-----------------|  
|**\<fichier_entrée>**|Spécifie un fichier SQL Server Express .mdf, un fichier SQL Server Compact 3.5 .sdf, ou un fichier intermédiaire .dbml.|  
  
## <a name="remarks"></a>Notes  
 La fonctionnalité SqlMetal implique en fait deux étapes :  
  
- Extraction des métadonnées de la base de données dans un fichier .dbml.  
  
- Génération d'un fichier de sortie de code.  
  
     En utilisant les options de ligne de commande appropriées, vous pouvez produire du code source en Visual Basic ou C#, ou encore un fichier de mappage en XML.  
  
 Pour extraire les métadonnées d'un fichier .mdf, vous devez spécifier le nom du fichier .mdf après toutes les autres options.  
  
 Si **/server** n’est pas spécifié, **localhost/sqlexpress** est supposé.  
  
 Microsoft SQL Server 2005 lève une exception si au moins l’une des conditions suivantes est remplie :  
  
- SqlMetal essaie d'extraire une procédure stockée qui s'appelle elle-même.  
  
- Le niveau d'imbrication d'une procédure stockée, d'une fonction, ou d'une vue dépasse 32.  
  
     SqlMetal intercepte cette exception et la signale comme un avertissement.  
  
 Pour spécifier un nom de fichier d'entrée, ajoutez son nom à la ligne de commande comme fichier d'entrée. L’inclusion du nom de fichier dans la chaîne de connexion (avec l’option **/conn** ) n’est pas prise en charge.  
  
## <a name="examples"></a>Exemples  
 Générez un fichier .dbml qui inclut des métadonnées SQL extraites :  
  
 **sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**  
  
 Générez un fichier .dbml qui inclut des métadonnées SQL extraites d'un fichier .mdf à l'aide de SQL Server Express :  
  
 **sqlmetal /dbml:mymeta.dbml mydbfile.mdf**  
  
 Générez un fichier .dbml qui inclut des métadonnées SQL extraites de SQL Server Express :  
  
 **sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**  
  
 Générez du code source à partir d'un fichier de métadonnées .dbml :  
  
 **sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**  
  
 Générez le code source directement à partir de métadonnées SQL :  
  
 **sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
> Quand vous utilisez l’option **/pluralize** avec l’exemple de base de données Northwind, notez le comportement suivant. Lorsque SqlMetal génère des noms de types de lignes pour des tables, les noms de table sont au singulier. Lorsqu'il génère des propriétés <xref:System.Data.Linq.DataContext> pour des tables, les noms de table sont au pluriel. Par coïncidence, les tables de l'exemple de base de données Northwind sont déjà au pluriel. Par conséquent, vous ne pourrez pas voir cette partie active. Bien qu’il soit courant de nommer des tables de base de données au pluriel, il est également courant dans .NET de nommer des collections au pluriel.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour générer le modèle objet en Visual Basic ou C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [Génération de code dans LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Mappage externe](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
