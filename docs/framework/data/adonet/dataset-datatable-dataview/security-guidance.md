---
title: Aide sur la sécurité des jeux de données et des DataTable
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 24c8a830f8638bc2d9dd20c2384c8230a682d817
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812235"
---
# <a name="dataset-and-datatable-security-guidance"></a>Aide sur la sécurité des jeux de données et des DataTable

Cet article s’applique à :

* .NET Framework (toutes les versions)
* .NET Core et versions ultérieures
* .NET 5,0 et versions ultérieures

Les types [DataSet](/dotnet/api/system.data.dataset) et [DataTable](/dotnet/api/system.data.datatable) sont des composants .net hérités qui permettent de représenter les jeux de données comme des objets managés. Ces composants ont été introduits dans .NET 1,0 dans le cadre de l' [infrastructure ADO.net](/dotnet/framework/data/adonet/dataset-datatable-dataview/)d’origine. Son objectif était de fournir une vue managée sur un jeu de données relationnelles, en faisant abstraction de la source de données sous-jacente XML, SQL ou une autre technologie.

Pour plus d’informations sur ADO.NET, y compris des paradigmes d’affichage de données plus modernes, consultez [la documentation de ADO.net](/dotnet/framework/data/adonet/).

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a>Restrictions par défaut lors de la désérialisation d’un DataSet ou d’un DataTable à partir de XML

Sur toutes les versions prises en charge de .NET Framework, .NET Core et .NET, `DataSet` et `DataTable` Placez les restrictions suivantes sur les types d’objets qui peuvent être présents dans les données désérialisées. Par défaut, cette liste est limitée à :

* Primitives et équivalents primitifs : `bool` , `char` , `sbyte` , `byte` , `short` , `ushort` , `int` , `uint` , `long` ,,,,,, `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, et.
* Non primitives couramment utilisées : `Type` , `Uri` et `BigInteger` .
* Types _System. Drawing_ couramment utilisés `Color` : `Point` , `PointF` ,,,, `Rectangle` `RectangleF` `Size` et `SizeF` .
* `Enum` modes.
* Tableaux et listes des types ci-dessus.

Si les données XML entrantes contiennent un objet dont le type n’est pas dans cette liste :

* Une exception est levée avec le message et la trace de la pile suivants.  
Message d’erreur :  
System. InvalidOperationException : type' \<Type Name\> , version = \<n.n.n.n\> , culture = \<culture\> , PublicKeyToken = \<token value\> 'n’est pas autorisé ici. [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227)Pour plus d’informations, consultez.  
Trace de la pile :  
dans System. Data. TypeLimiter. EnsureTypeIsAllowed (type type, TypeLimiter capturedLimiter)  
à System. Data. DataColumn. UpdateColumnType (type type, StorageType typeCode)  
à System. Data. DataColumn. set_DataType (valeur de type)  

* L’opération de désérialisation échoue.

Lors du chargement de données XML dans une `DataSet` instance ou existante `DataTable` , les définitions de colonne existantes sont également prises en compte. Si la table contient déjà une définition de colonne d’un type personnalisé, ce type est ajouté temporairement à la liste verte pour la durée de l’opération de désérialisation XML.

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

Les restrictions de type d’objet s’appliquent également lorsque `XmlSerializer` vous utilisez pour désérialiser une instance de `DataSet` ou `DataTable` . Toutefois, ils peuvent ne pas s’appliquer lors de l’utilisation `BinaryFormatter` de pour désérialiser une instance de `DataSet` ou `DataTable` .

Les restrictions de type d’objet ne s’appliquent pas lors de l’utilisation de `DataAdapter.Fill` , par exemple lorsqu’une `DataTable` instance est remplie directement à partir d’une base de données sans utiliser les API de désérialisation XML.

### <a name="extend-the-list-of-allowed-types"></a>Étendre la liste des types autorisés

Une application peut étendre la liste des types autorisés pour inclure des types personnalisés en plus des types intégrés répertoriés ci-dessus. Si vous étendez la liste des types autorisés, la modification affecte _toutes les_ `DataSet` `DataTable` instances et dans l’application. Les types ne peuvent pas être supprimés de la liste des types intégrés autorisés.

#### <a name="extend-through-configuration-net-framework-40---48"></a>Étendre la configuration (.NET Framework 4,0-4,8)

_App.config_ peut être utilisé pour étendre la liste des types autorisés. Pour étendre la liste des types autorisés :

* Utilisez l' `<configSections>` élément pour ajouter une référence à la section de configuration _System. Data_ .
* Utilisez `<system.data.dataset.serialization>` / `<allowedTypes>` pour spécifier des types supplémentaires.

Chaque `<add>` élément doit spécifier un seul type en utilisant son nom de type qualifié d’assembly. Pour ajouter des types supplémentaires à la liste des types autorisés, utilisez plusieurs `<add>` éléments.

L’exemple suivant illustre l’extension de la liste des types autorisés en ajoutant le type personnalisé `Fabrikam.CustomType` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Pour récupérer le nom qualifié d’assembly d’un type, utilisez la propriété [type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) , comme illustré dans le code suivant.

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a>Étendre la configuration (.NET Framework 2,0-3,5)

Si votre application cible .NET Framework 2,0 ou 3,5, vous pouvez toujours utiliser le mécanisme de _App.config_ ci-dessus pour étendre la liste des types autorisés. Toutefois, l' `<configSections>` apparence de votre élément sera légèrement différente, comme illustré dans le code suivant :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a>Étendre par programme (.NET Framework, .NET Core, .NET 5.0 +)

La liste des types autorisés peut également être étendue par programme en utilisant [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) avec la clé connue _System. Data. DataSetDefaultAllowedTypes_, comme illustré dans le code suivant.

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

Si vous utilisez le mécanisme d’extension, la valeur associée à la clé _System. Data. DataSetDefaultAllowedTypes_ doit être de type `Type[]` .

Sur .NET Framework, la liste des types autorisés peut être étendue à la fois avec _App.config_ et `AppDomain.SetData` . Dans ce cas, `DataSet` et `DataTable` permet à un objet d’être désérialisé dans le cadre des données si son type est présent dans l’une ou l’autre des listes.

### <a name="run-an-app-in-audit-mode-net-framework"></a>Exécuter une application en mode audit (.NET Framework)

Dans .NET Framework, `DataSet` et `DataTable` fournissent une fonctionnalité de mode audit. Lorsque le mode audit est activé, `DataSet` et `DataTable` Comparez les types d’objets entrants à la liste types autorisés. Toutefois, si un objet dont le type n’est pas autorisé est visible **, aucune exception n’est levée.** Au lieu `DataSet` de `DataTable` cela, et notifient toutes les instances attachées `TraceListener` qu’un type suspect est présent, ce qui permet au `TraceListener` d’enregistrer ces informations. Aucune exception n’est levée et l’opération de désérialisation continue.

> [!WARNING]
> L’exécution d’une application en « mode audit » ne doit être qu’une mesure temporaire utilisée pour le test. Lorsque le mode d’audit est activé, `DataSet` et `DataTable` n’appliquent pas les restrictions de type, ce qui peut introduire une faille de sécurité dans votre application. Pour plus d’informations, consultez les sections intitulées [Suppression de toutes les restrictions de type](#ratr) et [sécurité en ce qui concerne les entrées non approuvées](#swr).

Le mode audit peut être activé via _App.config_:

* Pour plus d’informations sur la valeur appropriée à placer pour l’élément, consultez la section extension de la [configuration](#etc) dans ce document `<configSections>` .
* Utilisez `<allowedTypes auditOnly="true">` pour activer le mode audit, comme indiqué dans le balisage suivant.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Une fois le mode d’audit activé, vous pouvez utiliser _App.config_ pour connecter votre favori `TraceListener` au `DataSet` nom intégré `TraceSource.` de la source de suivi intégrée est _System. Data. DataSet_. L’exemple suivant illustre l’écriture d’événements de trace sur la console _et_ dans un fichier journal sur le disque.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

Pour plus d’informations sur `TraceSource` et `TraceListener` , consultez le document [Comment : utiliser des TraceSource et des filtres avec des écouteurs de suivi](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).

> [!NOTE]
> L’exécution d’une application en mode audit n’est pas disponible dans .NET Core ni dans .NET 5,0 et versions ultérieures.

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a>Supprimer toutes les restrictions de type

Si une application doit supprimer toutes les restrictions de limitation de type de `DataSet` et `DataTable` :

* Il existe plusieurs options pour supprimer les restrictions de limitation de type.
* Les options disponibles dépendent du Framework ciblé par l’application.

> [!WARNING]
> La suppression de toutes les restrictions de type peut introduire une faille de sécurité à l’intérieur de l’application. Lors de l’utilisation de ce mécanisme, assurez-vous que l’application n’utilise **pas** `DataSet` ou `DataTable` pour lire les entrées non fiables. Pour plus d’informations, consultez [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) et la section suivante intitulée [sécurité en ce qui concerne les entrées non approuvées](#swr).

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a>Via la configuration de AppContext (.NET Framework 4,6-4,8, .NET Core 2,1 et versions ultérieures, .NET 5,0 et versions ultérieures)

Le `AppContext` commutateur, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` , lorsqu’il est défini sur `true` supprime toutes les restrictions de limitation de type de `DataSet` et `DataTable` .

Dans .NET Framework, ce commutateur peut être activé via _App.config_, comme indiqué dans la configuration suivante :

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

Dans ASP.NET, l' `<AppContextSwitchOverrides>` élément n’est pas disponible. Au lieu de cela, le commutateur peut être activé via _Web.config_, comme indiqué dans la configuration suivante :

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

Pour plus d’informations, consultez l' [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément.

Dans .NET Core, .NET 5 et ASP.NET Core, ce paramètre est contrôlé par _runtimeconfig.js_, comme illustré dans le code JSON suivant :

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

Pour plus d’informations, consultez [« paramètres de configuration du Runtime .net Core »](/dotnet/core/run-time-config/).

`AllowArbitraryDataSetTypeInstantiation` vous pouvez également définir par programme par le biais de [AppContext. SetSwitch](/dotnet/api/system.appcontext.setswitch) au lieu d’utiliser un fichier de configuration, comme indiqué dans le code suivant :

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 Si vous choisissez l’approche de programmation précédente, l’appel à `AppContext.SetSwitch` doit se produire tôt au démarrage des applications.

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a>Par le biais du Registre au niveau de l’ordinateur (.NET Framework 2,0-4,8)

Si `AppContext` n’est pas disponible, les contrôles de limite de type peuvent être désactivés avec le Registre Windows :

* Un administrateur doit configurer le registre.
* L’utilisation du Registre est une modification à l’ensemble de l’ordinateur et affecte _toutes les_ applications qui s’exécutent sur l’ordinateur.

| Type  |  Valeur |
|---|---|
| **Clé de Registre** | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| **Nom de la valeur** | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| **Type de valeur** | `REG_SZ` |
| **Données de valeur** | `true` |

Sur un système d’exploitation 64 bits, vous devez ajouter cette valeur pour la clé de 64 bits (illustrée ci-dessus) et la clé de 32 bits. La clé 32 bits se trouve à l’emplacement `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .

Pour plus d’informations sur l’utilisation du Registre pour configurer `AppContext` , consultez [« AppContext for Library Consumers »](/dotnet/api/system.appcontext#appcontext-for-library-consumers)(en anglais).

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a>Sécurité en ce qui concerne les entrées non fiables

Bien que `DataSet` et `DataTable` imposent des limitations par défaut sur les types qui sont autorisés à être présents lors de la désérialisation des charges utiles XML, __ `DataSet` et `DataTable` qui ne sont généralement pas sécurisés quand ils sont remplis avec une entrée non fiable.__ Voici une liste non exhaustive des façons dont une `DataSet` `DataTable` instance ou peut lire des entrées non fiables.

* `DataAdapter`Fait référence à une base de données, et la `DataAdapter.Fill` méthode est utilisée pour remplir un `DataSet` avec le contenu d’une requête de base de données.
* La `DataSet.ReadXml` `DataTable.ReadXml` méthode ou est utilisée pour lire un fichier XML contenant des informations sur les colonnes et les lignes.
* Une `DataSet` `DataTable` instance ou est sérialisée dans le cadre d’un ASP.net (SOAP) Web services ou d’un point de terminaison WCF.
* Un sérialiseur tel que `XmlSerializer` est utilisé pour désérialiser une `DataSet` `DataTable` instance ou à partir d’un flux XML.
* Un sérialiseur tel que `JsonConvert` est utilisé pour désérialiser une `DataSet` `DataTable` instance ou à partir d’un flux JSON. `JsonConvert` est une méthode dans leNewtonsoft.Jstiers populaire [ sur](https://www.newtonsoft.com/json) la bibliothèque.
* Un sérialiseur tel que `BinaryFormatter` est utilisé pour désérialiser une `DataSet` `DataTable` instance ou à partir d’un flux d’octets bruts.

Ce document aborde les considérations de sécurité pour les scénarios précédents.

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a>Utilisez `DataAdapter.Fill` pour remplir un `DataSet` à partir d’une source de données non approuvée

Une `DataSet` instance peut être remplie à partir d’un à `DataAdapter` l’aide de [la `DataAdapter.Fill` méthode](/dotnet/api/system.data.common.dataadapter.fill), comme indiqué dans l’exemple suivant.

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

(L’exemple de code ci-dessus fait partie d’un exemple plus large trouvé dans [remplissage d’un DataSet à partir d’un DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)

> La plupart des applications peuvent simplifier et supposer que leur couche de base de données est approuvée. Toutefois, si vous êtes en l’habitude de la [modélisation des menaces](https://www.microsoft.com/securityengineering/sdl/threatmodeling) de vos applications, votre modèle de menace peut considérer qu’il y a une limite d’approbation entre l’application (client) et la couche de base de données (serveur). L’utilisation de l' [authentification mutuelle](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) ou de [l’authentification AAD](/azure/azure-sql/database/authentication-aad-overview) entre le client et le serveur est un moyen d’aider à résoudre les risques associés à ce. Le reste de cette section décrit le résultat possible d’un client qui se connecte à un serveur non fiable.

Les conséquences du pointage sur une `DataAdapter` source de données non approuvée dépendent de l’implémentation du `DataAdapter` lui-même.

### <a name="sqldataadapter"></a>SqlDataAdapter

Pour le type intégré [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), la référence à une source de données non approuvée peut entraîner une attaque par déni de service (dos). L’attaque DoS peut entraîner un blocage ou une panne de l’application. Si une personne malveillante peut planter une DLL parallèlement à l’application, elle peut également être en mesure d’effectuer l’exécution du code local.

### <a name="other-dataadapter-types"></a>Autres types DataAdapter

`DataAdapter`Les implémentations tierces doivent faire leurs propres évaluations sur les garanties de sécurité qu’elles fournissent en matière d’entrées non approuvées. .NET ne peut apporter aucune garantie de sécurité concernant ces implémentations.

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a>DataSet. ReadXml et DataTable. ReadXml

Les `DataSet.ReadXml` `DataTable.ReadXml` méthodes et ne sont pas sécurisées quand elles sont utilisées avec une entrée non fiable. Nous vous recommandons vivement d’utiliser l’une des alternatives décrites plus loin dans ce document.

Les implémentations de `DataSet.ReadXml` et `DataTable.ReadXml` ont été créées à l’origine avant que les vulnérabilités de sérialisation soient une catégorie de menace bien comprise. Par conséquent, le code ne suit pas les meilleures pratiques de sécurité actuelles. Ces API peuvent être utilisées comme vecteurs pour permettre aux attaquants d’effectuer des attaques DoS sur des applications Web. Ces attaques peuvent rendre le service Web sans réponse ou entraîner un arrêt inattendu du processus. L’infrastructure ne fournit pas d’atténuation pour ces catégories d’attaques et .NET considère ce comportement « par conception ».

.NET a publié des mises à jour de sécurité pour limiter certains problèmes, tels que la divulgation d’informations ou l’exécution de code à distance dans `DataSet.ReadXml` et `DataTable.ReadXml` . Les mises à jour de sécurité .NET peuvent ne pas fournir une protection complète contre ces catégories de menaces. Les consommateurs doivent évaluer leurs scénarios individuels et prendre en compte leur exposition potentielle à ces risques.

Les consommateurs doivent savoir que les mises à jour de sécurité de ces API peuvent avoir un impact sur la compatibilité des applications dans certaines situations. En outre, il est possible qu’une nouvelle vulnérabilité dans ces API soit découverte pour laquelle .NET ne peut pas pratiquement publier une mise à jour de sécurité.

Nous recommandons aux consommateurs de ces API :

* Envisagez d’utiliser l’une des solutions décrites plus loin dans ce document.
* Effectuez des évaluations des risques individuels sur leurs applications.

La seule responsabilité du consommateur est de déterminer s’il faut utiliser ces API. Les consommateurs doivent évaluer les risques de sécurité, techniques et juridiques, y compris les exigences réglementaires, qui peuvent accompagner l’utilisation de ces API.

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a>DataSet et DataTable via les services Web ASP.NET ou WCF

Il est possible d’accepter une `DataSet` instance ou `DataTable` dans un service Web ASP.net (SOAP), comme illustré dans le code suivant :

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

Une variante de cette valeur n’accepte pas `DataSet` ou `DataTable` directement en tant que paramètre, mais plutôt de l’accepter dans le cadre du graphique d’objets sérialisés SOAP global, comme illustré dans le code suivant :

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Ou, à l’aide de WCF au lieu de services Web ASP.NET :

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Dans tous ces cas, le modèle de menace et les garanties de sécurité sont les mêmes que la [section DataSet. ReadXml et DataTable. ReadXml](#dsrdtr).

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a>Désérialiser un DataSet ou un DataTable via XmlSerializer

Les développeurs peuvent utiliser `XmlSerializer` pour désérialiser les `DataSet` `DataTable` instances et, comme illustré dans le code suivant :

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Dans ce cas, le modèle de menace et les garanties de sécurité sont les mêmes que la [section DataSet. ReadXml et DataTable. ReadXml.](#dsrdtr)

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a>Désérialiser un DataSet ou un DataTable via JsonConvert

Le [JSON.net](https://www.newtonsoft.com/json) de la bibliothèque Newtonsoft tiers populaire peut être utilisé pour désérialiser `DataSet` les `DataTable` instances et, comme le montre le code suivant :

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

La désérialisation d' `DataSet` un `DataTable` objet ou de cette façon à partir d’un objet BLOB JSON non approuvé n’est pas sécurisée. Ce modèle est vulnérable à une attaque par déni de service. Une telle attaque peut entraîner le blocage de l’application ou l’affichage d’une absence de réponse.

> [!NOTE]
> Microsoft ne garantit pas ou ne prend pas en charge l’implémentation de bibliothèques tierces comme _Newtonsoft.Jssur_. Ces informations sont fournies à des fins d’exhaustivité et sont précises au moment de la rédaction de cet article.

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a>Désérialiser un DataSet ou un DataTable via BinaryFormatter

Les développeurs ne doivent jamais utiliser `BinaryFormatter` ,, `NetDataContractSerializer` `SoapFormatter` ou des formateurs ***non sécurisés*** associés pour désérialiser une `DataSet` `DataTable` instance ou à partir d’une charge utile non fiable :

* Cela est vulnérable à une attaque d’exécution de code à distance complète.
* L’utilisation d’un personnalisé `SerializationBinder` n’est pas suffisante pour empêcher une telle attaque.

## <a name="safe-replacements"></a>Remplacements sécurisés

Pour les applications qui :

* Acceptez `DataSet` ou `DataTable` via un point de terminaison SOAP. asmx ou un point de terminaison WCF.
* Désérialiser les données non approuvées dans une instance de `DataSet` ou `DataTable` .

Envisagez de remplacer le modèle objet pour utiliser [Entity Framework](/ef). Entity Framework:

* Est une infrastructure riche et moderne, orientée objet, qui peut représenter des données relationnelles.
* Apporte [un vaste écosystème](/ef/core/providers/) de fournisseurs de bases de données pour faciliter le projet de requêtes de base de données via vos modèles objet Entity Framework.
* Offre des protections intégrées lors de la désérialisation de données provenant de sources non approuvées.

Pour les applications qui utilisent des `.aspx` points de terminaison SOAP, pensez à modifier ces points de terminaison pour utiliser [WCF](/dotnet/framework/wcf/). WCF est un substitut plus complet pour les `.asmx` services Web. Les points de terminaison WCF [peuvent être exposés via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) à des fins de compatibilité avec les appelants existants.

## <a name="code-analyzers"></a>Analyseurs de code

Les règles de sécurité de l’analyseur de code, qui s’exécutent lors de la compilation de votre code source, peuvent aider à identifier les vulnérabilités liées à ce problème de sécurité en C# et Visual Basic code. Microsoft. CodeAnalysis. FxCopAnalyzers est un package NuGet d’analyseurs de code qui est distribué sur [NuGet.org](https://www.nuget.org/).

Pour obtenir une vue d’ensemble des analyseurs de code, consultez [vue d’ensemble des analyseurs de code source](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).

Activez les règles Microsoft. CodeAnalysis. FxCopAnalyzers suivantes :

- [Ca2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): n’utilisez pas DataTable. ReadXml () avec des données non fiables
- [Ca2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): n’utilisez pas DataSet. ReadXml () avec des données non fiables
- [CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): un jeu de données ou un DataTable non sécurisé dans un type sérialisable peut être vulnérable aux attaques par exécution de code à distance
- [CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): jeu de données ou DataTable non sécurisés dans le type sérialisable
- [CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): un jeu de données ou un DataTable non sécurisé dans un graphique d’objets désérialisé peut être vulnérable aux attaques d’exécution de code à distance
- [CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): type DataSet ou DataTable non sécurisé trouvé dans le graphique d’objets désérialisable
- [CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): DataSet ou type DataTable non sécurisé dans le graphique d’objets désérialisable Web
- [CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Vérifiez que la classe générée automatiquement contenant DataSet. ReadXml () n’est pas utilisée avec des données non fiables
- [CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): un jeu de données ou un DataTable non sécurisé dans un type sérialisable généré automatiquement peut être vulnérable aux attaques d’exécution de code à distance

Pour plus d’informations sur la configuration des règles, consultez [utiliser des analyseurs de code](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).

Les nouvelles règles de sécurité sont disponibles dans les packages NuGet suivants :

- Microsoft. CodeAnalysis. FxCopAnalyzers 3.3.0 : pour Visual Studio 2019 version 16,3 ou ultérieure
- Microsoft. CodeAnalysis. FxCopAnalyzers 2.9.11 : pour Visual Studio 2017 version 15,9 ou ultérieure
