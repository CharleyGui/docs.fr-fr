---
title: Aide sur la sécurité des jeux de données et des DataTable
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: f0fa43c467cc7866e69115acb5f807e6487fda7a
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608526"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="1732b-102">Aide sur la sécurité des jeux de données et des DataTable</span><span class="sxs-lookup"><span data-stu-id="1732b-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="1732b-103">Cet article s’applique à :</span><span class="sxs-lookup"><span data-stu-id="1732b-103">This article applies to:</span></span>

* <span data-ttu-id="1732b-104">.NET Framework (toutes les versions)</span><span class="sxs-lookup"><span data-stu-id="1732b-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="1732b-105">.NET Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="1732b-105">.NET Core and later</span></span>
* <span data-ttu-id="1732b-106">.NET 5,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="1732b-106">.NET 5.0 and later</span></span>

<span data-ttu-id="1732b-107">Les types [DataSet](/dotnet/api/system.data.dataset) et [DataTable](/dotnet/api/system.data.datatable) sont des composants .net hérités qui permettent de représenter les jeux de données comme des objets managés.</span><span class="sxs-lookup"><span data-stu-id="1732b-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="1732b-108">Ces composants ont été introduits dans .NET 1,0 dans le cadre de l' [infrastructure ADO.net](/dotnet/framework/data/adonet/dataset-datatable-dataview/)d’origine.</span><span class="sxs-lookup"><span data-stu-id="1732b-108">These components were introduced in .NET 1.0 as part of the original [ADO.NET infrastructure](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span></span> <span data-ttu-id="1732b-109">Son objectif était de fournir une vue managée sur un jeu de données relationnelles, en faisant abstraction de la source de données sous-jacente XML, SQL ou une autre technologie.</span><span class="sxs-lookup"><span data-stu-id="1732b-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="1732b-110">Pour plus d’informations sur ADO.NET, y compris des paradigmes d’affichage de données plus modernes, consultez [la documentation de ADO.net](/dotnet/framework/data/adonet/).</span><span class="sxs-lookup"><span data-stu-id="1732b-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](/dotnet/framework/data/adonet/).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="1732b-111">Restrictions par défaut lors de la désérialisation d’un DataSet ou d’un DataTable à partir de XML</span><span class="sxs-lookup"><span data-stu-id="1732b-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="1732b-112">Sur toutes les versions prises en charge de .NET Framework, .NET Core et .NET, `DataSet` et `DataTable` Placez les restrictions suivantes sur les types d’objets qui peuvent être présents dans les données désérialisées.</span><span class="sxs-lookup"><span data-stu-id="1732b-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="1732b-113">Par défaut, cette liste est limitée à :</span><span class="sxs-lookup"><span data-stu-id="1732b-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="1732b-114">Primitives et équivalents primitifs : `bool` , `char` , `sbyte` , `byte` , `short` , `ushort` , `int` , `uint` , `long` ,,,,,, `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, et.</span><span class="sxs-lookup"><span data-stu-id="1732b-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="1732b-115">Non primitives couramment utilisées : `Type` , `Uri` et `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="1732b-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="1732b-116">Types _System. Drawing_ couramment utilisés `Color` : `Point` , `PointF` ,,,, `Rectangle` `RectangleF` `Size` et `SizeF` .</span><span class="sxs-lookup"><span data-stu-id="1732b-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="1732b-117">`Enum` modes.</span><span class="sxs-lookup"><span data-stu-id="1732b-117">`Enum` types.</span></span>
* <span data-ttu-id="1732b-118">Tableaux et listes des types ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="1732b-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="1732b-119">Si les données XML entrantes contiennent un objet dont le type n’est pas dans cette liste :</span><span class="sxs-lookup"><span data-stu-id="1732b-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="1732b-120">Une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="1732b-120">An exception is thrown.</span></span>
* <span data-ttu-id="1732b-121">L’opération de désérialisation échoue.</span><span class="sxs-lookup"><span data-stu-id="1732b-121">The deserialization operation fails.</span></span>

<span data-ttu-id="1732b-122">Lors du chargement de données XML dans une `DataSet` instance ou existante `DataTable` , les définitions de colonne existantes sont également prises en compte.</span><span class="sxs-lookup"><span data-stu-id="1732b-122">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="1732b-123">Si la table contient déjà une définition de colonne d’un type personnalisé, ce type est ajouté temporairement à la liste verte pour la durée de l’opération de désérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="1732b-123">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

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

<span data-ttu-id="1732b-124">Les restrictions de type d’objet s’appliquent également lorsque `XmlSerializer` vous utilisez pour désérialiser une instance de `DataSet` ou `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="1732b-124">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="1732b-125">Toutefois, ils peuvent ne pas s’appliquer lors de l’utilisation `BinaryFormatter` de pour désérialiser une instance de `DataSet` ou `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="1732b-125">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="1732b-126">Les restrictions de type d’objet ne s’appliquent pas lors de l’utilisation de `DataAdapter.Fill` , par exemple lorsqu’une `DataTable` instance est remplie directement à partir d’une base de données sans utiliser les API de désérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="1732b-126">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="1732b-127">Étendre la liste des types autorisés</span><span class="sxs-lookup"><span data-stu-id="1732b-127">Extend the list of allowed types</span></span>

<span data-ttu-id="1732b-128">Une application peut étendre la liste des types autorisés pour inclure des types personnalisés en plus des types intégrés répertoriés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="1732b-128">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="1732b-129">Si vous étendez la liste des types autorisés, la modification affecte _toutes les_ `DataSet` `DataTable` instances et dans l’application.</span><span class="sxs-lookup"><span data-stu-id="1732b-129">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="1732b-130">Les types ne peuvent pas être supprimés de la liste des types intégrés autorisés.</span><span class="sxs-lookup"><span data-stu-id="1732b-130">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="1732b-131">Étendre la configuration (.NET Framework 4,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="1732b-131">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="1732b-132">_App.config_ peut être utilisé pour étendre la liste des types autorisés.</span><span class="sxs-lookup"><span data-stu-id="1732b-132">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="1732b-133">Pour étendre la liste des types autorisés :</span><span class="sxs-lookup"><span data-stu-id="1732b-133">To extend the allowed types list:</span></span>

* <span data-ttu-id="1732b-134">Utilisez l' `<configSections>` élément pour ajouter une référence à la section de configuration _System. Data_ .</span><span class="sxs-lookup"><span data-stu-id="1732b-134">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="1732b-135">Utilisez `<system.data.dataset.serialization>` / `<allowedTypes>` pour spécifier des types supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1732b-135">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="1732b-136">Chaque `<add>` élément doit spécifier un seul type en utilisant son nom de type qualifié d’assembly.</span><span class="sxs-lookup"><span data-stu-id="1732b-136">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="1732b-137">Pour ajouter des types supplémentaires à la liste des types autorisés, utilisez plusieurs `<add>` éléments.</span><span class="sxs-lookup"><span data-stu-id="1732b-137">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="1732b-138">L’exemple suivant illustre l’extension de la liste des types autorisés en ajoutant le type personnalisé `Fabrikam.CustomType` .</span><span class="sxs-lookup"><span data-stu-id="1732b-138">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

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

<span data-ttu-id="1732b-139">Pour récupérer le nom qualifié d’assembly d’un type, utilisez la propriété [type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) , comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1732b-139">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="1732b-140">Étendre la configuration (.NET Framework 2,0-3,5)</span><span class="sxs-lookup"><span data-stu-id="1732b-140">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="1732b-141">Si votre application cible .NET Framework 2,0 ou 3,5, vous pouvez toujours utiliser le mécanisme de _App.config_ ci-dessus pour étendre la liste des types autorisés.</span><span class="sxs-lookup"><span data-stu-id="1732b-141">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="1732b-142">Toutefois, l' `<configSections>` apparence de votre élément sera légèrement différente, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1732b-142">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

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

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="1732b-143">Étendre par programme (.NET Framework, .NET Core, .NET 5.0 +)</span><span class="sxs-lookup"><span data-stu-id="1732b-143">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="1732b-144">La liste des types autorisés peut également être étendue par programme en utilisant [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) avec la clé connue _System. Data. DataSetDefaultAllowedTypes_, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1732b-144">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="1732b-145">Si vous utilisez le mécanisme d’extension, la valeur associée à la clé _System. Data. DataSetDefaultAllowedTypes_ doit être de type `Type[]` .</span><span class="sxs-lookup"><span data-stu-id="1732b-145">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="1732b-146">Sur .NET Framework, la liste des types autorisés peut être étendue à la fois avec _App.config_ et `AppDomain.SetData` .</span><span class="sxs-lookup"><span data-stu-id="1732b-146">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="1732b-147">Dans ce cas, `DataSet` et `DataTable` permet à un objet d’être désérialisé dans le cadre des données si son type est présent dans l’une ou l’autre des listes.</span><span class="sxs-lookup"><span data-stu-id="1732b-147">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="1732b-148">Exécuter une application en mode audit (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="1732b-148">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="1732b-149">Dans .NET Framework, `DataSet` et `DataTable` fournissent une fonctionnalité de mode audit.</span><span class="sxs-lookup"><span data-stu-id="1732b-149">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="1732b-150">Lorsque le mode audit est activé, `DataSet` et `DataTable` Comparez les types d’objets entrants à la liste types autorisés.</span><span class="sxs-lookup"><span data-stu-id="1732b-150">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="1732b-151">Toutefois, si un objet dont le type n’est pas autorisé est visible **, aucune exception n’est levée.**</span><span class="sxs-lookup"><span data-stu-id="1732b-151">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="1732b-152">Au lieu `DataSet` de `DataTable` cela, et notifient toutes les instances attachées `TraceListener` qu’un type suspect est présent, ce qui permet au `TraceListener` d’enregistrer ces informations.</span><span class="sxs-lookup"><span data-stu-id="1732b-152">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="1732b-153">Aucune exception n’est levée et l’opération de désérialisation continue.</span><span class="sxs-lookup"><span data-stu-id="1732b-153">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="1732b-154">L’exécution d’une application en « mode audit » ne doit être qu’une mesure temporaire utilisée pour le test.</span><span class="sxs-lookup"><span data-stu-id="1732b-154">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="1732b-155">Lorsque le mode d’audit est activé, `DataSet` et `DataTable` n’appliquent pas les restrictions de type, ce qui peut introduire une faille de sécurité dans votre application.</span><span class="sxs-lookup"><span data-stu-id="1732b-155">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="1732b-156">Pour plus d’informations, consultez les sections intitulées [Suppression de toutes les restrictions de type](#ratr) et [sécurité en ce qui concerne les entrées non approuvées](#swr).</span><span class="sxs-lookup"><span data-stu-id="1732b-156">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="1732b-157">Le mode audit peut être activé via _App.config_:</span><span class="sxs-lookup"><span data-stu-id="1732b-157">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="1732b-158">Pour plus d’informations sur la valeur appropriée à placer pour l’élément, consultez la section extension de la [configuration](#etc) dans ce document `<configSections>` .</span><span class="sxs-lookup"><span data-stu-id="1732b-158">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="1732b-159">Utilisez `<allowedTypes auditOnly="true">` pour activer le mode audit, comme indiqué dans le balisage suivant.</span><span class="sxs-lookup"><span data-stu-id="1732b-159">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

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

<span data-ttu-id="1732b-160">Une fois le mode d’audit activé, vous pouvez utiliser _App.config_ pour connecter votre favori `TraceListener` au `DataSet` nom intégré `TraceSource.` de la source de suivi intégrée est _System. Data. DataSet_.</span><span class="sxs-lookup"><span data-stu-id="1732b-160">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="1732b-161">L’exemple suivant illustre l’écriture d’événements de trace sur la console _et_ dans un fichier journal sur le disque.</span><span class="sxs-lookup"><span data-stu-id="1732b-161">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

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

<span data-ttu-id="1732b-162">Pour plus d’informations sur `TraceSource` et `TraceListener` , consultez le document [Comment : utiliser des TraceSource et des filtres avec des écouteurs de suivi](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="1732b-162">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1732b-163">L’exécution d’une application en mode audit n’est pas disponible dans .NET Core ni dans .NET 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1732b-163">Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="1732b-164">Supprimer toutes les restrictions de type</span><span class="sxs-lookup"><span data-stu-id="1732b-164">Remove all type restrictions</span></span>

<span data-ttu-id="1732b-165">Si une application doit supprimer toutes les restrictions de limitation de type de `DataSet` et `DataTable` :</span><span class="sxs-lookup"><span data-stu-id="1732b-165">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="1732b-166">Il existe plusieurs options pour supprimer les restrictions de limitation de type.</span><span class="sxs-lookup"><span data-stu-id="1732b-166">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="1732b-167">Les options disponibles dépendent du Framework ciblé par l’application.</span><span class="sxs-lookup"><span data-stu-id="1732b-167">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="1732b-168">La suppression de toutes les restrictions de type peut introduire une faille de sécurité à l’intérieur de l’application.</span><span class="sxs-lookup"><span data-stu-id="1732b-168">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="1732b-169">Lors de l’utilisation de ce mécanisme, assurez-vous que l’application n’utilise **pas** `DataSet` ou `DataTable` pour lire les entrées non fiables.</span><span class="sxs-lookup"><span data-stu-id="1732b-169">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="1732b-170">Pour plus d’informations, consultez [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) et la section suivante intitulée [sécurité en ce qui concerne les entrées non approuvées](#swr).</span><span class="sxs-lookup"><span data-stu-id="1732b-170">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="1732b-171">Via la configuration de AppContext (.NET Framework 4,6-4,8, .NET Core 2,1 et versions ultérieures, .NET 5,0 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="1732b-171">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="1732b-172">Le `AppContext` commutateur, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` , lorsqu’il est défini sur `true` supprime toutes les restrictions de limitation de type de `DataSet` et `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="1732b-172">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="1732b-173">Dans .NET Framework, ce commutateur peut être activé via _App.config_, comme indiqué dans la configuration suivante :</span><span class="sxs-lookup"><span data-stu-id="1732b-173">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="1732b-174">Dans ASP.NET, l' `<AppContextSwitchOverrides>` élément n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="1732b-174">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="1732b-175">Au lieu de cela, le commutateur peut être activé via _Web.config_, comme indiqué dans la configuration suivante :</span><span class="sxs-lookup"><span data-stu-id="1732b-175">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="1732b-176">Pour plus d’informations, consultez l' [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="1732b-176">For more information, see the [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element.</span></span>

<span data-ttu-id="1732b-177">Dans .NET Core, .NET 5 et ASP.NET Core, ce paramètre est contrôlé par _runtimeconfig.js_, comme illustré dans le code JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="1732b-177">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="1732b-178">Pour plus d’informations, consultez [« paramètres de configuration du Runtime .net Core »](/dotnet/core/run-time-config/).</span><span class="sxs-lookup"><span data-stu-id="1732b-178">For more information, see [".NET Core run-time configuration settings"](/dotnet/core/run-time-config/).</span></span>

<span data-ttu-id="1732b-179">`AllowArbitraryDataSetTypeInstantiation` vous pouvez également définir par programme par le biais de [AppContext. SetSwitch](/dotnet/api/system.appcontext.setswitch) au lieu d’utiliser un fichier de configuration, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1732b-179">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="1732b-180">Si vous choisissez l’approche de programmation précédente, l’appel à `AppContext.SetSwitch` doit se produire tôt au démarrage des applications.</span><span class="sxs-lookup"><span data-stu-id="1732b-180">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="1732b-181">Par le biais du Registre au niveau de l’ordinateur (.NET Framework 2,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="1732b-181">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="1732b-182">Si `AppContext` n’est pas disponible, les contrôles de limite de type peuvent être désactivés avec le Registre Windows :</span><span class="sxs-lookup"><span data-stu-id="1732b-182">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="1732b-183">Un administrateur doit configurer le registre.</span><span class="sxs-lookup"><span data-stu-id="1732b-183">An administrator must configure the registry.</span></span>
* <span data-ttu-id="1732b-184">L’utilisation du Registre est une modification à l’ensemble de l’ordinateur et affecte _toutes les_ applications qui s’exécutent sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1732b-184">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="1732b-185">Type</span><span class="sxs-lookup"><span data-stu-id="1732b-185">Type</span></span>  |  <span data-ttu-id="1732b-186">Valeur</span><span class="sxs-lookup"><span data-stu-id="1732b-186">Value</span></span> |
|---|---|
| <span data-ttu-id="1732b-187">**Clé de Registre**</span><span class="sxs-lookup"><span data-stu-id="1732b-187">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="1732b-188">**Nom de la valeur**</span><span class="sxs-lookup"><span data-stu-id="1732b-188">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="1732b-189">**Type de valeur**</span><span class="sxs-lookup"><span data-stu-id="1732b-189">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="1732b-190">**Données de valeur**</span><span class="sxs-lookup"><span data-stu-id="1732b-190">**Value data**</span></span> | `true` |

<span data-ttu-id="1732b-191">Sur un système d’exploitation 64 bits, vous devez ajouter cette valeur pour la clé de 64 bits (illustrée ci-dessus) et la clé de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="1732b-191">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="1732b-192">La clé 32 bits se trouve à l’emplacement `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .</span><span class="sxs-lookup"><span data-stu-id="1732b-192">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="1732b-193">Pour plus d’informations sur l’utilisation du Registre pour configurer `AppContext` , consultez [« AppContext for Library Consumers »](/dotnet/api/system.appcontext#appcontext-for-library-consumers)(en anglais).</span><span class="sxs-lookup"><span data-stu-id="1732b-193">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="1732b-194">Sécurité en ce qui concerne les entrées non fiables</span><span class="sxs-lookup"><span data-stu-id="1732b-194">Safety with regard to untrusted input</span></span>

<span data-ttu-id="1732b-195">Bien que `DataSet` et `DataTable` imposent des limitations par défaut sur les types qui sont autorisés à être présents lors de la désérialisation des charges utiles XML, __ `DataSet` et `DataTable` qui ne sont généralement pas sécurisés quand ils sont remplis avec une entrée non fiable.__</span><span class="sxs-lookup"><span data-stu-id="1732b-195">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="1732b-196">Voici une liste non exhaustive des façons dont une `DataSet` `DataTable` instance ou peut lire des entrées non fiables.</span><span class="sxs-lookup"><span data-stu-id="1732b-196">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="1732b-197">`DataAdapter`Fait référence à une base de données, et la `DataAdapter.Fill` méthode est utilisée pour remplir un `DataSet` avec le contenu d’une requête de base de données.</span><span class="sxs-lookup"><span data-stu-id="1732b-197">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="1732b-198">La `DataSet.ReadXml` `DataTable.ReadXml` méthode ou est utilisée pour lire un fichier XML contenant des informations sur les colonnes et les lignes.</span><span class="sxs-lookup"><span data-stu-id="1732b-198">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="1732b-199">Une `DataSet` `DataTable` instance ou est sérialisée dans le cadre d’un ASP.net (SOAP) Web services ou d’un point de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="1732b-199">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="1732b-200">Un sérialiseur tel que `XmlSerializer` est utilisé pour désérialiser une `DataSet` `DataTable` instance ou à partir d’un flux XML.</span><span class="sxs-lookup"><span data-stu-id="1732b-200">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="1732b-201">Un sérialiseur tel que `JsonConvert` est utilisé pour désérialiser une `DataSet` `DataTable` instance ou à partir d’un flux JSON.</span><span class="sxs-lookup"><span data-stu-id="1732b-201">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="1732b-202">`JsonConvert` est une méthode dans leNewtonsoft.Jstiers populaire [ sur](https://www.newtonsoft.com/json) la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="1732b-202">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="1732b-203">Un sérialiseur tel que `BinaryFormatter` est utilisé pour désérialiser une `DataSet` `DataTable` instance ou à partir d’un flux d’octets bruts.</span><span class="sxs-lookup"><span data-stu-id="1732b-203">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="1732b-204">Ce document aborde les considérations de sécurité pour les scénarios précédents.</span><span class="sxs-lookup"><span data-stu-id="1732b-204">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="1732b-205">Utilisez `DataAdapter.Fill` pour remplir un `DataSet` à partir d’une source de données non approuvée</span><span class="sxs-lookup"><span data-stu-id="1732b-205">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="1732b-206">Une `DataSet` instance peut être remplie à partir d’un à `DataAdapter` l’aide de [la `DataAdapter.Fill` méthode](/dotnet/api/system.data.common.dataadapter.fill), comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1732b-206">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="1732b-207">(L’exemple de code ci-dessus fait partie d’un exemple plus large trouvé dans [remplissage d’un DataSet à partir d’un DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span><span class="sxs-lookup"><span data-stu-id="1732b-207">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span></span>

> <span data-ttu-id="1732b-208">La plupart des applications peuvent simplifier et supposer que leur couche de base de données est approuvée.</span><span class="sxs-lookup"><span data-stu-id="1732b-208">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="1732b-209">Toutefois, si vous êtes en l’habitude de la [modélisation des menaces](https://www.microsoft.com/securityengineering/sdl/threatmodeling) de vos applications, votre modèle de menace peut considérer qu’il y a une limite d’approbation entre l’application (client) et la couche de base de données (serveur).</span><span class="sxs-lookup"><span data-stu-id="1732b-209">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="1732b-210">L’utilisation de l' [authentification mutuelle](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) ou de [l’authentification AAD](/azure/azure-sql/database/authentication-aad-overview) entre le client et le serveur est un moyen d’aider à résoudre les risques associés à ce.</span><span class="sxs-lookup"><span data-stu-id="1732b-210">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="1732b-211">Le reste de cette section décrit le résultat possible d’un client qui se connecte à un serveur non fiable.</span><span class="sxs-lookup"><span data-stu-id="1732b-211">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="1732b-212">Les conséquences du pointage sur une `DataAdapter` source de données non approuvée dépendent de l’implémentation du `DataAdapter` lui-même.</span><span class="sxs-lookup"><span data-stu-id="1732b-212">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="1732b-213">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="1732b-213">SqlDataAdapter</span></span>

<span data-ttu-id="1732b-214">Pour le type intégré [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), la référence à une source de données non approuvée peut entraîner une attaque par déni de service (dos).</span><span class="sxs-lookup"><span data-stu-id="1732b-214">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="1732b-215">L’attaque DoS peut entraîner un blocage ou une panne de l’application.</span><span class="sxs-lookup"><span data-stu-id="1732b-215">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="1732b-216">Si une personne malveillante peut planter une DLL parallèlement à l’application, elle peut également être en mesure d’effectuer l’exécution du code local.</span><span class="sxs-lookup"><span data-stu-id="1732b-216">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="1732b-217">Autres types DataAdapter</span><span class="sxs-lookup"><span data-stu-id="1732b-217">Other DataAdapter types</span></span>

<span data-ttu-id="1732b-218">`DataAdapter`Les implémentations tierces doivent faire leurs propres évaluations sur les garanties de sécurité qu’elles fournissent en matière d’entrées non approuvées.</span><span class="sxs-lookup"><span data-stu-id="1732b-218">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="1732b-219">.NET ne peut apporter aucune garantie de sécurité concernant ces implémentations.</span><span class="sxs-lookup"><span data-stu-id="1732b-219">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="1732b-220">DataSet. ReadXml et DataTable. ReadXml</span><span class="sxs-lookup"><span data-stu-id="1732b-220">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="1732b-221">Les `DataSet.ReadXml` `DataTable.ReadXml` méthodes et ne sont pas sécurisées quand elles sont utilisées avec une entrée non fiable.</span><span class="sxs-lookup"><span data-stu-id="1732b-221">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="1732b-222">Nous vous recommandons vivement d’utiliser l’une des alternatives décrites plus loin dans ce document.</span><span class="sxs-lookup"><span data-stu-id="1732b-222">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="1732b-223">Les implémentations de `DataSet.ReadXml` et `DataTable.ReadXml` ont été créées à l’origine avant que les vulnérabilités de sérialisation soient une catégorie de menace bien comprise.</span><span class="sxs-lookup"><span data-stu-id="1732b-223">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="1732b-224">Par conséquent, le code ne suit pas les meilleures pratiques de sécurité actuelles.</span><span class="sxs-lookup"><span data-stu-id="1732b-224">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="1732b-225">Ces API peuvent être utilisées comme vecteurs pour permettre aux attaquants d’effectuer des attaques DoS sur des applications Web.</span><span class="sxs-lookup"><span data-stu-id="1732b-225">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="1732b-226">Ces attaques peuvent rendre le service Web sans réponse ou entraîner un arrêt inattendu du processus.</span><span class="sxs-lookup"><span data-stu-id="1732b-226">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="1732b-227">L’infrastructure ne fournit pas d’atténuation pour ces catégories d’attaques et .NET considère ce comportement « par conception ».</span><span class="sxs-lookup"><span data-stu-id="1732b-227">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="1732b-228">.NET a publié des mises à jour de sécurité pour limiter certains problèmes, tels que la divulgation d’informations ou l’exécution de code à distance dans `DataSet.ReadXml` et `DataTable.ReadXml` .</span><span class="sxs-lookup"><span data-stu-id="1732b-228">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="1732b-229">Les mises à jour de sécurité .NET peuvent ne pas fournir une protection complète contre ces catégories de menaces.</span><span class="sxs-lookup"><span data-stu-id="1732b-229">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="1732b-230">Les consommateurs doivent évaluer leurs scénarios individuels et prendre en compte leur exposition potentielle à ces risques.</span><span class="sxs-lookup"><span data-stu-id="1732b-230">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="1732b-231">Les consommateurs doivent savoir que les mises à jour de sécurité de ces API peuvent avoir un impact sur la compatibilité des applications dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="1732b-231">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="1732b-232">En outre, il est possible qu’une nouvelle vulnérabilité dans ces API soit découverte pour laquelle .NET ne peut pas pratiquement publier une mise à jour de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1732b-232">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="1732b-233">Nous recommandons aux consommateurs de ces API :</span><span class="sxs-lookup"><span data-stu-id="1732b-233">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="1732b-234">Envisagez d’utiliser l’une des solutions décrites plus loin dans ce document.</span><span class="sxs-lookup"><span data-stu-id="1732b-234">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="1732b-235">Effectuez des évaluations des risques individuels sur leurs applications.</span><span class="sxs-lookup"><span data-stu-id="1732b-235">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="1732b-236">La seule responsabilité du consommateur est de déterminer s’il faut utiliser ces API.</span><span class="sxs-lookup"><span data-stu-id="1732b-236">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="1732b-237">Les consommateurs doivent évaluer les risques de sécurité, techniques et juridiques, y compris les exigences réglementaires, qui peuvent accompagner l’utilisation de ces API.</span><span class="sxs-lookup"><span data-stu-id="1732b-237">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="1732b-238">DataSet et DataTable via les services Web ASP.NET ou WCF</span><span class="sxs-lookup"><span data-stu-id="1732b-238">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="1732b-239">Il est possible d’accepter une `DataSet` instance ou `DataTable` dans un service Web ASP.net (SOAP), comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1732b-239">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

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

<span data-ttu-id="1732b-240">Une variante de cette valeur n’accepte pas `DataSet` ou `DataTable` directement en tant que paramètre, mais plutôt de l’accepter dans le cadre du graphique d’objets sérialisés SOAP global, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1732b-240">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

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

<span data-ttu-id="1732b-241">Ou, à l’aide de WCF au lieu de services Web ASP.NET :</span><span class="sxs-lookup"><span data-stu-id="1732b-241">Or, using WCF instead of ASP.NET web services:</span></span>

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

<span data-ttu-id="1732b-242">Dans tous ces cas, le modèle de menace et les garanties de sécurité sont les mêmes que la [section DataSet. ReadXml et DataTable. ReadXml](#dsrdtr).</span><span class="sxs-lookup"><span data-stu-id="1732b-242">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="1732b-243">Désérialiser un DataSet ou un DataTable via XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="1732b-243">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="1732b-244">Les développeurs peuvent utiliser `XmlSerializer` pour désérialiser les `DataSet` `DataTable` instances et, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1732b-244">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

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

<span data-ttu-id="1732b-245">Dans ce cas, le modèle de menace et les garanties de sécurité sont les mêmes que la [section DataSet. ReadXml et DataTable. ReadXml.](#dsrdtr)</span><span class="sxs-lookup"><span data-stu-id="1732b-245">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="1732b-246">Désérialiser un DataSet ou un DataTable via JsonConvert</span><span class="sxs-lookup"><span data-stu-id="1732b-246">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="1732b-247">Le [JSON.net](https://www.newtonsoft.com/json) de la bibliothèque Newtonsoft tiers populaire peut être utilisé pour désérialiser `DataSet` les `DataTable` instances et, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1732b-247">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

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

<span data-ttu-id="1732b-248">La désérialisation d' `DataSet` un `DataTable` objet ou de cette façon à partir d’un objet BLOB JSON non approuvé n’est pas sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1732b-248">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="1732b-249">Ce modèle est vulnérable à une attaque par déni de service.</span><span class="sxs-lookup"><span data-stu-id="1732b-249">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="1732b-250">Une telle attaque peut entraîner le blocage de l’application ou l’affichage d’une absence de réponse.</span><span class="sxs-lookup"><span data-stu-id="1732b-250">Such an attack could crash the app or render it unresponsive.</span></span>

> [!NOTE]
> <span data-ttu-id="1732b-251">Microsoft ne garantit pas ou ne prend pas en charge l’implémentation de bibliothèques tierces comme _Newtonsoft.Jssur_.</span><span class="sxs-lookup"><span data-stu-id="1732b-251">Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="1732b-252">Ces informations sont fournies à des fins d’exhaustivité et sont précises au moment de la rédaction de cet article.</span><span class="sxs-lookup"><span data-stu-id="1732b-252">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="1732b-253">Désérialiser un DataSet ou un DataTable via BinaryFormatter</span><span class="sxs-lookup"><span data-stu-id="1732b-253">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="1732b-254">Les développeurs ne doivent jamais utiliser `BinaryFormatter` ,, `NetDataContractSerializer` `SoapFormatter` ou des formateurs ***non sécurisés*** associés pour désérialiser une `DataSet` `DataTable` instance ou à partir d’une charge utile non fiable :</span><span class="sxs-lookup"><span data-stu-id="1732b-254">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related ***unsafe*** formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

* <span data-ttu-id="1732b-255">Cela est vulnérable à une attaque d’exécution de code à distance complète.</span><span class="sxs-lookup"><span data-stu-id="1732b-255">This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="1732b-256">L’utilisation d’un personnalisé `SerializationBinder` n’est pas suffisante pour empêcher une telle attaque.</span><span class="sxs-lookup"><span data-stu-id="1732b-256">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="1732b-257">Remplacements sécurisés</span><span class="sxs-lookup"><span data-stu-id="1732b-257">Safe replacements</span></span>

<span data-ttu-id="1732b-258">Pour les applications qui :</span><span class="sxs-lookup"><span data-stu-id="1732b-258">For apps that either:</span></span>

* <span data-ttu-id="1732b-259">Acceptez `DataSet` ou `DataTable` via un point de terminaison SOAP. asmx ou un point de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="1732b-259">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="1732b-260">Désérialiser les données non approuvées dans une instance de `DataSet` ou `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="1732b-260">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="1732b-261">Envisagez de remplacer le modèle objet pour utiliser [Entity Framework](/ef).</span><span class="sxs-lookup"><span data-stu-id="1732b-261">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="1732b-262">Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="1732b-262">Entity Framework:</span></span>

* <span data-ttu-id="1732b-263">Est une infrastructure riche et moderne, orientée objet, qui peut représenter des données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="1732b-263">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="1732b-264">Apporte [un vaste écosystème](/ef/core/providers/) de fournisseurs de bases de données pour faciliter le projet de requêtes de base de données via vos modèles objet Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1732b-264">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="1732b-265">Offre des protections intégrées lors de la désérialisation de données provenant de sources non approuvées.</span><span class="sxs-lookup"><span data-stu-id="1732b-265">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="1732b-266">Pour les applications qui utilisent des `.aspx` points de terminaison SOAP, pensez à modifier ces points de terminaison pour utiliser [WCF](/dotnet/framework/wcf/).</span><span class="sxs-lookup"><span data-stu-id="1732b-266">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](/dotnet/framework/wcf/).</span></span> <span data-ttu-id="1732b-267">WCF est un substitut plus complet pour les `.asmx` services Web.</span><span class="sxs-lookup"><span data-stu-id="1732b-267">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="1732b-268">Les points de terminaison WCF [peuvent être exposés via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) à des fins de compatibilité avec les appelants existants.</span><span class="sxs-lookup"><span data-stu-id="1732b-268">WCF endpoints [can be exposed via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) for compatibility with existing callers.</span></span>

## <a name="code-analyzers"></a><span data-ttu-id="1732b-269">Analyseurs de code</span><span class="sxs-lookup"><span data-stu-id="1732b-269">Code analyzers</span></span>

<span data-ttu-id="1732b-270">Les règles de sécurité de l’analyseur de code, qui s’exécutent lors de la compilation de votre code source, peuvent aider à identifier les vulnérabilités liées à ce problème de sécurité en C# et Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="1732b-270">Code analyzer security rules, which run when your source code is compiled, can help to find vulnerabilities related to this security issue in C# and Visual Basic code.</span></span> <span data-ttu-id="1732b-271">Microsoft. CodeAnalysis. FxCopAnalyzers est un package NuGet d’analyseurs de code qui est distribué sur [NuGet.org](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="1732b-271">Microsoft.CodeAnalysis.FxCopAnalyzers is a NuGet package of code analyzers that's distributed on [nuget.org](https://www.nuget.org/).</span></span>

<span data-ttu-id="1732b-272">Pour obtenir une vue d’ensemble des analyseurs de code, consultez [vue d’ensemble des analyseurs de code source](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span><span class="sxs-lookup"><span data-stu-id="1732b-272">For an overview of code analyzers, see [Overview of source code analyzers](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

<span data-ttu-id="1732b-273">Activez les règles Microsoft. CodeAnalysis. FxCopAnalyzers suivantes :</span><span class="sxs-lookup"><span data-stu-id="1732b-273">Enable the following Microsoft.CodeAnalysis.FxCopAnalyzers rules:</span></span>

- <span data-ttu-id="1732b-274">[Ca2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): n’utilisez pas DataTable. ReadXml () avec des données non fiables</span><span class="sxs-lookup"><span data-stu-id="1732b-274">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): Do not use DataTable.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="1732b-275">[Ca2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): n’utilisez pas DataSet. ReadXml () avec des données non fiables</span><span class="sxs-lookup"><span data-stu-id="1732b-275">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): Do not use DataSet.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="1732b-276">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): un jeu de données ou un DataTable non sécurisé dans un type sérialisable peut être vulnérable aux attaques par exécution de code à distance</span><span class="sxs-lookup"><span data-stu-id="1732b-276">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): Unsafe DataSet or DataTable in serializable type can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="1732b-277">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): jeu de données ou DataTable non sécurisés dans le type sérialisable</span><span class="sxs-lookup"><span data-stu-id="1732b-277">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): Unsafe DataSet or DataTable in serializable type</span></span>
- <span data-ttu-id="1732b-278">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): un jeu de données ou un DataTable non sécurisé dans un graphique d’objets désérialisé peut être vulnérable aux attaques d’exécution de code à distance</span><span class="sxs-lookup"><span data-stu-id="1732b-278">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): Unsafe DataSet or DataTable in deserialized object graph can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="1732b-279">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): type DataSet ou DataTable non sécurisé trouvé dans le graphique d’objets désérialisable</span><span class="sxs-lookup"><span data-stu-id="1732b-279">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): Unsafe DataSet or DataTable type found in deserializable object graph</span></span>
- <span data-ttu-id="1732b-280">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): DataSet ou type DataTable non sécurisé dans le graphique d’objets désérialisable Web</span><span class="sxs-lookup"><span data-stu-id="1732b-280">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): Unsafe DataSet or DataTable type in web deserializable object graph</span></span>
- <span data-ttu-id="1732b-281">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Vérifiez que la classe générée automatiquement contenant DataSet. ReadXml () n’est pas utilisée avec des données non fiables</span><span class="sxs-lookup"><span data-stu-id="1732b-281">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Ensure autogenerated class containing DataSet.ReadXml() is not used with untrusted data</span></span>
- <span data-ttu-id="1732b-282">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): un jeu de données ou un DataTable non sécurisé dans un type sérialisable généré automatiquement peut être vulnérable aux attaques d’exécution de code à distance</span><span class="sxs-lookup"><span data-stu-id="1732b-282">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): Unsafe DataSet or DataTable in autogenerated serializable type can be vulnerable to remote code execution attacks</span></span>

<span data-ttu-id="1732b-283">Pour plus d’informations sur la configuration des règles, consultez [utiliser des analyseurs de code](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span><span class="sxs-lookup"><span data-stu-id="1732b-283">For more information about configuring rules, see [Use code analyzers](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span></span>

<span data-ttu-id="1732b-284">Les nouvelles règles de sécurité sont disponibles dans les packages NuGet suivants :</span><span class="sxs-lookup"><span data-stu-id="1732b-284">The new security rules are available in the following NuGet packages:</span></span>

- <span data-ttu-id="1732b-285">Microsoft. CodeAnalysis. FxCopAnalyzers 3.3.0 : pour Visual Studio 2019 version 16,3 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="1732b-285">Microsoft.CodeAnalysis.FxCopAnalyzers 3.3.0: for Visual Studio 2019 version 16.3 or later</span></span>
- <span data-ttu-id="1732b-286">Microsoft. CodeAnalysis. FxCopAnalyzers 2.9.11 : pour Visual Studio 2017 version 15,9 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="1732b-286">Microsoft.CodeAnalysis.FxCopAnalyzers 2.9.11: for Visual Studio 2017 version 15.9 or later</span></span>
