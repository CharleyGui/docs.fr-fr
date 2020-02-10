---
title: Activités d'accès aux bases de données
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: ed3f0ad3f2fd19f622c9cb0faf7d5cd864b81995
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094642"
---
# <a name="database-access-activities"></a><span data-ttu-id="ca094-102">Activités d'accès aux bases de données</span><span class="sxs-lookup"><span data-stu-id="ca094-102">Database Access Activities</span></span>

<span data-ttu-id="ca094-103">Les activités d'accès aux bases de données vous permettent d'accéder à une base de données dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="ca094-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="ca094-104">Ces activités permettent d’accéder aux bases de données afin de récupérer ou de modifier des informations et d’utiliser [ADO.net](../../data/adonet/index.md) pour accéder à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ca094-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca094-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ca094-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ca094-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ca094-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ca094-107">Si ce répertoire n’existe pas, accédez à la page de téléchargement pour télécharger tous les exemples de Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ca094-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca094-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ca094-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="ca094-109">Activités de base de données</span><span class="sxs-lookup"><span data-stu-id="ca094-109">Database Activities</span></span>

<span data-ttu-id="ca094-110">Les sections suivantes détaillent la liste des activités incluses dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ca094-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="ca094-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="ca094-111">DbUpdate</span></span>

<span data-ttu-id="ca094-112">Exécute une requête SQL qui produit une modification dans la base de données (insertion, mise à jour, suppression et autres modifications).</span><span class="sxs-lookup"><span data-stu-id="ca094-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="ca094-113">Cette classe effectue son travail de façon asynchrone (elle dérive d'<xref:System.Activities.AsyncCodeActivity> et utilise ses fonctionnalités asynchrones).</span><span class="sxs-lookup"><span data-stu-id="ca094-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="ca094-114">Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="ca094-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="ca094-115">La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="ca094-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="ca094-116">Une fois `DbUpdate` exécuté, le nombre des enregistrements affectés est retourné dans la propriété `AffectedRecords`.</span><span class="sxs-lookup"><span data-stu-id="ca094-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```csharp
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="ca094-117">Argument</span><span class="sxs-lookup"><span data-stu-id="ca094-117">Argument</span></span>|<span data-ttu-id="ca094-118">Description</span><span class="sxs-lookup"><span data-stu-id="ca094-118">Description</span></span>|
|-|-|
|<span data-ttu-id="ca094-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="ca094-119">ProviderName</span></span>|<span data-ttu-id="ca094-120">Nom invariant du fournisseur ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ca094-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="ca094-121">Si cet argument est défini, `ConnectionString` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="ca094-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="ca094-122">ConnectionString</span></span>|<span data-ttu-id="ca094-123">Chaîne de connexion utilisée pour se connecter à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ca094-123">Connection string to connect to the database.</span></span> <span data-ttu-id="ca094-124">Si cet argument est défini, `ProviderName` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="ca094-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="ca094-125">ConfigName</span></span>|<span data-ttu-id="ca094-126">Nom de la section du fichier de configuration où les informations de connexion sont stockées.</span><span class="sxs-lookup"><span data-stu-id="ca094-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="ca094-127">Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.</span><span class="sxs-lookup"><span data-stu-id="ca094-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="ca094-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="ca094-128">CommandType</span></span>|<span data-ttu-id="ca094-129">Type du <xref:System.Data.Common.DbCommand> à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="ca094-130">SQL</span><span class="sxs-lookup"><span data-stu-id="ca094-130">Sql</span></span>|<span data-ttu-id="ca094-131">Commande SQL à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="ca094-132">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca094-132">Parameters</span></span>|<span data-ttu-id="ca094-133">Collection des paramètres de la requête SQL.</span><span class="sxs-lookup"><span data-stu-id="ca094-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="ca094-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="ca094-134">AffectedRecords</span></span>|<span data-ttu-id="ca094-135">Nombre d'enregistrements affectés par la dernière opération.</span><span class="sxs-lookup"><span data-stu-id="ca094-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="ca094-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="ca094-136">DbQueryScalar</span></span>

<span data-ttu-id="ca094-137">Exécute une requête qui récupère une valeur unique à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="ca094-137">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="ca094-138">Cette classe effectue son travail de façon asynchrone (elle dérive d'<xref:System.Activities.AsyncCodeActivity%601> et utilise ses fonctionnalités asynchrones).</span><span class="sxs-lookup"><span data-stu-id="ca094-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="ca094-139">Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="ca094-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="ca094-140">La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="ca094-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="ca094-141">Après l’exécution de `DbQueryScalar`, le scalaire est retourné dans l’argument `Result out` (de type `TResult`, qui est défini dans la classe de base <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="ca094-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="ca094-142">Argument</span><span class="sxs-lookup"><span data-stu-id="ca094-142">Argument</span></span>|<span data-ttu-id="ca094-143">Description</span><span class="sxs-lookup"><span data-stu-id="ca094-143">Description</span></span>|
|-|-|
|<span data-ttu-id="ca094-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="ca094-144">ProviderName</span></span>|<span data-ttu-id="ca094-145">Nom invariant du fournisseur ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ca094-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="ca094-146">Si cet argument est défini, `ConnectionString` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="ca094-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="ca094-147">ConnectionString</span></span>|<span data-ttu-id="ca094-148">Chaîne de connexion utilisée pour se connecter à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ca094-148">Connection string to connect to the database.</span></span> <span data-ttu-id="ca094-149">Si cet argument est défini, `ProviderName` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="ca094-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="ca094-150">ConfigName</span></span>|<span data-ttu-id="ca094-151">Nom de la section du fichier de configuration où les informations de connexion sont stockées.</span><span class="sxs-lookup"><span data-stu-id="ca094-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="ca094-152">Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.</span><span class="sxs-lookup"><span data-stu-id="ca094-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="ca094-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="ca094-153">CommandType</span></span>|<span data-ttu-id="ca094-154">Type du <xref:System.Data.Common.DbCommand> à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="ca094-155">SQL</span><span class="sxs-lookup"><span data-stu-id="ca094-155">Sql</span></span>|<span data-ttu-id="ca094-156">Commande SQL à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="ca094-157">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca094-157">Parameters</span></span>|<span data-ttu-id="ca094-158">Collection des paramètres de la requête SQL.</span><span class="sxs-lookup"><span data-stu-id="ca094-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="ca094-159">Résultats</span><span class="sxs-lookup"><span data-stu-id="ca094-159">Result</span></span>|<span data-ttu-id="ca094-160">Scalaire obtenu une fois la requête exécutée.</span><span class="sxs-lookup"><span data-stu-id="ca094-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="ca094-161">Cet argument est de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="ca094-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="ca094-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="ca094-162">DbQuery</span></span>

<span data-ttu-id="ca094-163">Exécute une requête qui récupère une liste d'objets.</span><span class="sxs-lookup"><span data-stu-id="ca094-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="ca094-164">Une fois la requête exécutée, une fonction de mappage est exécutée (elle peut être <xref:System.Func%601><`DbDataReader`, `TResult`> ou un <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="ca094-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="ca094-165">Cette fonction de mappage obtient un enregistrement dans un `DbDataReader` et le mappe à l'objet à retourner.</span><span class="sxs-lookup"><span data-stu-id="ca094-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="ca094-166">Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="ca094-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="ca094-167">La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="ca094-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="ca094-168">Les résultats de la requête SQL sont récupérés à l'aide d'un `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="ca094-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="ca094-169">L'activité itère au sein de `DbDataReader` et mappe les lignes de `DbDataReader` à une instance de `TResult`.</span><span class="sxs-lookup"><span data-stu-id="ca094-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="ca094-170">L’utilisateur de `DbQuery` doit fournir le code de mappage. cette opération peut être effectuée de deux façons : à l’aide d’un <xref:System.Func%601><`DbDataReader`, `TResult`> ou d’un <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`>.</span><span class="sxs-lookup"><span data-stu-id="ca094-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="ca094-171">Dans le premier cas, le mappage est effectué en une seule impulsion d'exécution.</span><span class="sxs-lookup"><span data-stu-id="ca094-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="ca094-172">Par conséquent, il est plus rapide, mais ne peut pas être sérialisé en XAML.</span><span class="sxs-lookup"><span data-stu-id="ca094-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="ca094-173">Dans le dernier cas, le mappage est effectué en plusieurs impulsions.</span><span class="sxs-lookup"><span data-stu-id="ca094-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="ca094-174">Par conséquent, il peut être plus lent mais peut être sérialisé en XAML et créé de façon déclarative (toute activité existante peut participer au mappage).</span><span class="sxs-lookup"><span data-stu-id="ca094-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```csharp
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="ca094-175">Argument</span><span class="sxs-lookup"><span data-stu-id="ca094-175">Argument</span></span>|<span data-ttu-id="ca094-176">Description</span><span class="sxs-lookup"><span data-stu-id="ca094-176">Description</span></span>|
|-|-|
|<span data-ttu-id="ca094-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="ca094-177">ProviderName</span></span>|<span data-ttu-id="ca094-178">Nom invariant du fournisseur ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ca094-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="ca094-179">Si cet argument est défini, `ConnectionString` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="ca094-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="ca094-180">ConnectionString</span></span>|<span data-ttu-id="ca094-181">Chaîne de connexion utilisée pour se connecter à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ca094-181">Connection string to connect to the database.</span></span> <span data-ttu-id="ca094-182">Si cet argument est défini, `ProviderName` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="ca094-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="ca094-183">ConfigName</span></span>|<span data-ttu-id="ca094-184">Nom de la section du fichier de configuration où les informations de connexion sont stockées.</span><span class="sxs-lookup"><span data-stu-id="ca094-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="ca094-185">Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.</span><span class="sxs-lookup"><span data-stu-id="ca094-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="ca094-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="ca094-186">CommandType</span></span>|<span data-ttu-id="ca094-187">Type du <xref:System.Data.Common.DbCommand> à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="ca094-188">SQL</span><span class="sxs-lookup"><span data-stu-id="ca094-188">Sql</span></span>|<span data-ttu-id="ca094-189">Commande SQL à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="ca094-190">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca094-190">Parameters</span></span>|<span data-ttu-id="ca094-191">Collection des paramètres de la requête SQL.</span><span class="sxs-lookup"><span data-stu-id="ca094-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="ca094-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="ca094-192">Mapper</span></span>|<span data-ttu-id="ca094-193">Fonction de mappage (<xref:System.Func%601><`DbDataReader`, `TResult`>) qui prend un enregistrement dans le `DataReader` obtenu en tant que résultat de l’exécution de la requête et retourne une instance d’un objet de type `TResult` à ajouter à la collection `Result`.</span><span class="sxs-lookup"><span data-stu-id="ca094-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="ca094-194">Dans ce cas, le mappage est effectué en seule impulsion d'exécution, mais il ne peut pas être créé de façon déclarative à l'aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="ca094-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="ca094-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="ca094-195">MapperFunc</span></span>|<span data-ttu-id="ca094-196">Fonction de mappage (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) qui prend un enregistrement dans le `DataReader` obtenu en tant que résultat de l’exécution de la requête et retourne une instance d’un objet de type `TResult` à ajouter à la collection `Result`.</span><span class="sxs-lookup"><span data-stu-id="ca094-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="ca094-197">Dans ce cas, le mappage est effectué en plusieurs impulsions d'exécution.</span><span class="sxs-lookup"><span data-stu-id="ca094-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="ca094-198">Cette fonction peut être sérialisée en XAML et créée de façon déclarative (toute activité existante peut participer au mappage).</span><span class="sxs-lookup"><span data-stu-id="ca094-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="ca094-199">Résultats</span><span class="sxs-lookup"><span data-stu-id="ca094-199">Result</span></span>|<span data-ttu-id="ca094-200">Liste des objets obtenus en résultat de l'exécution de la requête et de l'exécution de la fonction de mappage pour chaque d'enregistrement de `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="ca094-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="ca094-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="ca094-201">DbQueryDataSet</span></span>

<span data-ttu-id="ca094-202">Exécute une requête qui retourne un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ca094-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ca094-203">Cette classe effectue son travail de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ca094-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="ca094-204">Il dérive de <xref:System.Activities.AsyncCodeActivity><`TResult`> et utilise ses fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="ca094-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="ca094-205">Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="ca094-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="ca094-206">La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="ca094-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="ca094-207">Une fois la `DbQueryDataSet` exécutée, le `DataSet` est retourné dans l’argument `Result out` (de type `TResult`, qui est défini dans la classe de base <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="ca094-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="ca094-208">Argument</span><span class="sxs-lookup"><span data-stu-id="ca094-208">Argument</span></span>|<span data-ttu-id="ca094-209">Description</span><span class="sxs-lookup"><span data-stu-id="ca094-209">Description</span></span>|
|-|-|
|<span data-ttu-id="ca094-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="ca094-210">ProviderName</span></span>|<span data-ttu-id="ca094-211">Nom invariant du fournisseur ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ca094-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="ca094-212">Si cet argument est défini, `ConnectionString` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="ca094-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="ca094-213">ConnectionString</span></span>|<span data-ttu-id="ca094-214">Chaîne de connexion utilisée pour se connecter à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ca094-214">Connection string to connect to the database.</span></span> <span data-ttu-id="ca094-215">Si cet argument est défini, `ProviderName` doit également être défini.</span><span class="sxs-lookup"><span data-stu-id="ca094-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="ca094-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="ca094-216">ConfigName</span></span>|<span data-ttu-id="ca094-217">Nom de la section du fichier de configuration où les informations de connexion sont stockées.</span><span class="sxs-lookup"><span data-stu-id="ca094-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="ca094-218">Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.</span><span class="sxs-lookup"><span data-stu-id="ca094-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="ca094-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="ca094-219">CommandType</span></span>|<span data-ttu-id="ca094-220">Type du <xref:System.Data.Common.DbCommand> à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="ca094-221">SQL</span><span class="sxs-lookup"><span data-stu-id="ca094-221">Sql</span></span>|<span data-ttu-id="ca094-222">Commande SQL à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca094-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="ca094-223">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca094-223">Parameters</span></span>|<span data-ttu-id="ca094-224">Collection des paramètres de la requête SQL.</span><span class="sxs-lookup"><span data-stu-id="ca094-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="ca094-225">Résultats</span><span class="sxs-lookup"><span data-stu-id="ca094-225">Result</span></span>|<span data-ttu-id="ca094-226"><xref:System.Data.DataSet> obtenu une fois la requête exécutée.</span><span class="sxs-lookup"><span data-stu-id="ca094-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="ca094-227">Configuration des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="ca094-227">Configuring Connection Information</span></span>

<span data-ttu-id="ca094-228">Tous les DbActivities partagent les mêmes paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="ca094-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="ca094-229">Ils peuvent être configurés de deux façons :</span><span class="sxs-lookup"><span data-stu-id="ca094-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="ca094-230">`ConnectionString + InvariantName` : définit le nom invariant du fournisseur ADO.NET et la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="ca094-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- <span data-ttu-id="ca094-231">`ConfigName` : définit le nom de la section de configuration qui contient les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="ca094-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="ca094-232">Dans l'activité :</span><span class="sxs-lookup"><span data-stu-id="ca094-232">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="ca094-233">Exécution de cet exemple</span><span class="sxs-lookup"><span data-stu-id="ca094-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="ca094-234">Instructions de configuration</span><span class="sxs-lookup"><span data-stu-id="ca094-234">Setup instructions</span></span>

<span data-ttu-id="ca094-235">Cet exemple utilise une base de données.</span><span class="sxs-lookup"><span data-stu-id="ca094-235">This sample uses a database.</span></span> <span data-ttu-id="ca094-236">Un script d'installation et de chargement (Setup.cmd) est fourni avec l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ca094-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="ca094-237">Vous devez exécuter ce fichier à l'aide de l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ca094-237">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="ca094-238">Le script Setup.cmd appelle le fichier de script CreateDb.sql, lequel contient des commandes SQL qui effectuent les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ca094-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="ca094-239">Crée une base de données appelée DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="ca094-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="ca094-240">Crée la table Roles.</span><span class="sxs-lookup"><span data-stu-id="ca094-240">Creates the Roles table.</span></span>

- <span data-ttu-id="ca094-241">Crée la table Employees.</span><span class="sxs-lookup"><span data-stu-id="ca094-241">Creates Employees table.</span></span>

- <span data-ttu-id="ca094-242">Insère trois enregistrements dans la table Roles.</span><span class="sxs-lookup"><span data-stu-id="ca094-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="ca094-243">Insère douze enregistrements dans la table Employees.</span><span class="sxs-lookup"><span data-stu-id="ca094-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="ca094-244">Pour exécuter Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="ca094-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="ca094-245">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ca094-245">Open a command prompt.</span></span>

2. <span data-ttu-id="ca094-246">Accédez au dossier d'exemples DbActivities.</span><span class="sxs-lookup"><span data-stu-id="ca094-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="ca094-247">Tapez « setup. cmd » et appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="ca094-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca094-248">Setup.cmd tente d'installer l'exemple dans l'instance SqlExpress de votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ca094-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="ca094-249">Si vous voulez l'installer dans une autre instance SQL Server, modifiez Setup.cmd avec le nom de la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="ca094-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="ca094-250">Pour désinstaller l'exemple de base de données</span><span class="sxs-lookup"><span data-stu-id="ca094-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="ca094-251">Exécutez le fichier Cleanup.cmd du dossier d’exemples dans une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ca094-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="ca094-252">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ca094-252">To run the sample</span></span>

1. <span data-ttu-id="ca094-253">Ouvrir la solution dans Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="ca094-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="ca094-254">Pour compiler la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="ca094-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="ca094-255">Pour exécuter l'exemple sans débogage, appuyez sur CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="ca094-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca094-256">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ca094-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ca094-257">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ca094-257">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ca094-258">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ca094-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca094-259">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ca094-259">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
