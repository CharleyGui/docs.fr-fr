---
title: Mise à jour des sources de données avec les DataAdapter
description: Découvrez comment la méthode de mise à jour de DataAdapter résout les modifications apportées à un jeu de données dans la source de données dans les applications ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286182"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="4708b-103">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="4708b-103">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="4708b-104">La méthode `Update` de l'objet <xref:System.Data.Common.DataAdapter> est appelée pour répercuter les modifications d'un objet <xref:System.Data.DataSet> dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="4708b-104">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="4708b-105">La méthode `Update`, comme la méthode `Fill`, prend comme arguments une instance d’un `DataSet` et un objet <xref:System.Data.DataTable> optionnel ou un nom de `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="4708b-105">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="4708b-106">L'instance `DataSet` est le `DataSet` qui contient les modifications apportées et le `DataTable` identifie la table de laquelle les modifications doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="4708b-106">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="4708b-107">Si aucun `DataTable` n'est spécifié, le premier `DataTable` du `DataSet` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4708b-107">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="4708b-108">Lorsque vous appelez la méthode `Update`, le `DataAdapter` analyse les modifications apportées et exécute la commande appropriée (INSERT, UPDATE ou DELETE).</span><span class="sxs-lookup"><span data-stu-id="4708b-108">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="4708b-109">Lorsque le `DataAdapter` rencontre une modification apportée à un objet <xref:System.Data.DataRow>, il utilise la propriété <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, ou <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> pour traiter la modification.</span><span class="sxs-lookup"><span data-stu-id="4708b-109">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="4708b-110">Cela vous permet d'optimiser les performances de votre application ADO.NET en spécifiant la syntaxe de commande au moment du design et, si possible, par le biais de l'utilisation de procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="4708b-110">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="4708b-111">Vous devez explicitement définir les commandes avant d'appeler la méthode `Update`.</span><span class="sxs-lookup"><span data-stu-id="4708b-111">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="4708b-112">Si la méthode `Update` est appelée et si la commande appropriée n'existe pas pour une mise à jour particulière (par exemple, pas de `DeleteCommand` pour les lignes supprimées), une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="4708b-112">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="4708b-113">Si vous utilisez des procédures stockées SQL Server pour modifier ou supprimer des données à l'aide de `DataAdapter`, assurez-vous que vous n'utilisez pas SET NOCOUNT ON dans la définition de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="4708b-113">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="4708b-114">En effet, le nombre de lignes affectées retourné serait alors la valeur zéro, ce que `DataAdapter` interprète comme un conflit d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="4708b-114">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="4708b-115">Dans ce cas, l'exception <xref:System.Data.DBConcurrencyException> est levée.</span><span class="sxs-lookup"><span data-stu-id="4708b-115">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="4708b-116">Des paramètres de commande peuvent être utilisés pour spécifier les valeurs d'entrée et de sortie d'une instruction SQL ou d'une procédure stockée pour chaque ligne modifiée dans un `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="4708b-116">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="4708b-117">Pour plus d’informations, consultez [paramètres DataAdapter](dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4708b-117">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4708b-118">Il est important de comprendre la différence entre la suppression d'une ligne dans un objet <xref:System.Data.DataTable> et la suppression de la ligne.</span><span class="sxs-lookup"><span data-stu-id="4708b-118">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="4708b-119">Lorsque vous appelez la méthode `Remove` ou `RemoveAt`, la ligne est immédiatement supprimée.</span><span class="sxs-lookup"><span data-stu-id="4708b-119">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="4708b-120">Aucune ligne correspondante dans la source de données principale ne sera affectée si vous passez ensuite le `DataTable` ou le `DataSet` à un `DataAdapter` et appelez la méthode `Update`.</span><span class="sxs-lookup"><span data-stu-id="4708b-120">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="4708b-121">Lorsque vous utilisez la méthode `Delete`, la ligne reste dans le `DataTable` et est marquée pour suppression.</span><span class="sxs-lookup"><span data-stu-id="4708b-121">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="4708b-122">Si vous passez ensuite le `DataTable` ou le `DataSet` à un `DataAdapter` et appelez la méthode `Update`, la ligne correspondante dans la source de données principale est supprimée.</span><span class="sxs-lookup"><span data-stu-id="4708b-122">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="4708b-123">Si votre `DataTable` est mappé à une table de base de données unique ou est généré par celle-ci, vous pouvez tirer parti de l'objet <xref:System.Data.Common.DbCommandBuilder> pour générer automatiquement les objets `DeleteCommand`, `InsertCommand` et `UpdateCommand` du `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="4708b-123">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="4708b-124">Pour plus d’informations, consultez [génération de commandes avec CommandBuilders](generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="4708b-124">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="4708b-125">Utilisation d'UpdatedRowSource pour mapper des valeurs à un DataSet</span><span class="sxs-lookup"><span data-stu-id="4708b-125">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="4708b-126">Vous pouvez contrôler la façon dont les valeurs retournées depuis la source de données sont de nouveau mappées au `DataTable` suite à un appel de la méthode Update d'un `DataAdapter`, en utilisant la propriété <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> d'un objet <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="4708b-126">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="4708b-127">En affectant l'une des valeurs d'énumération `UpdatedRowSource` à la propriété <xref:System.Data.UpdateRowSource>, vous pouvez contrôler si les paramètres de sortie retournés par les commandes `DataAdapter` sont ignorés ou appliqués à la ligne modifiée dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="4708b-127">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="4708b-128">Vous pouvez aussi spécifier si la première ligne retournée (si elle existe) doit être appliquée à la ligne modifiée dans le `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="4708b-128">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="4708b-129">Le tableau suivant décrit les différentes valeurs de l'énumération `UpdateRowSource` et la façon dont elles affectent le comportement d'une commande utilisée avec un `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="4708b-129">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="4708b-130">Énumération UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="4708b-130">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="4708b-131">Description</span><span class="sxs-lookup"><span data-stu-id="4708b-131">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="4708b-132">Les paramètres de sortie et la première ligne d'un jeu de résultats retourné peuvent être mappés à la ligne modifiée dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="4708b-132">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="4708b-133">Seules les données de la première ligne d'un jeu de résultats retourné peuvent être mappées à la ligne modifiée dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="4708b-133">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="4708b-134">Les paramètres de sortie ou les lignes d'un jeu de résultats retourné sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="4708b-134">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="4708b-135">Seuls les paramètres de sortie peuvent être mappés à la ligne modifiée dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="4708b-135">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="4708b-136">La méthode `Update` répercute vos modifications dans la source de données, cependant d'autres clients peuvent avoir modifié les données au niveau de la source depuis la dernière fois où vous avez rempli le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="4708b-136">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="4708b-137">Pour actualiser votre `DataSet` avec des données en cours, utilisez le `DataAdapter` et la méthode `Fill`.</span><span class="sxs-lookup"><span data-stu-id="4708b-137">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="4708b-138">De nouvelles lignes seront ajoutées à la table et les informations mises à jour seront incorporées dans les lignes existantes.</span><span class="sxs-lookup"><span data-stu-id="4708b-138">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="4708b-139">La méthode `Fill` détermine si une nouvelle ligne sera ajoutée ou si une ligne existante sera mise à jour en se basant sur les valeurs de clé primaire des lignes du `DataSet` et des lignes retournées par `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="4708b-139">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="4708b-140">Si une valeur de clé primaire d'une ligne du `Fill` correspond à celle d'une ligne des résultats retournés par `DataSet`, la méthode `SelectCommand` met à jour la ligne existante en y insérant les informations de la ligne retournée par `SelectCommand` et affecte la valeur <xref:System.Data.DataRow.RowState%2A> à la propriété `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="4708b-140">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="4708b-141">Si la valeur de clé primaire d'une ligne retournée par `SelectCommand` n'a pas de correspondance dans les lignes du `DataSet`, la méthode `Fill` ajoute une nouvelle ligne avec un `RowState` ayant la valeur `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="4708b-141">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="4708b-142">Si `SelectCommand` retourne les résultats d'un OUTER JOIN, le `DataAdapter` ne définit pas la valeur `PrimaryKey` du `DataTable` résultant.</span><span class="sxs-lookup"><span data-stu-id="4708b-142">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="4708b-143">Vous devez définir vous-même la `PrimaryKey` pour garantir une résolution correcte des lignes dupliquées.</span><span class="sxs-lookup"><span data-stu-id="4708b-143">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="4708b-144">Pour plus d’informations, consultez [définition des clés primaires](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="4708b-144">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="4708b-145">Pour gérer les exceptions qui peuvent se produire lors de l’appel de la `Update` méthode, vous pouvez utiliser l' `RowUpdated` événement pour répondre aux erreurs de mise à jour de ligne dès qu’elles se produisent (consultez [gestion des événements DataAdapter](handling-dataadapter-events.md)), ou vous pouvez affecter la valeur `DataAdapter.ContinueUpdateOnError` avant d' `true` appeler `Update` et répondre aux informations d’erreur stockées dans la `RowError` propriété d’une ligne particulière lorsque la mise à jour est terminée [Row Error Information](./dataset-datatable-dataview/row-error-information.md)</span><span class="sxs-lookup"><span data-stu-id="4708b-145">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="4708b-146">L’appel `AcceptChanges` de sur `DataSet` , `DataTable` ou `DataRow` entraîne le remplacement de toutes les `Original` valeurs d’un par `DataRow` les `Current` valeurs de `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="4708b-146">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="4708b-147">Si les valeurs de champ qui identifient la ligne comme étant unique ont été modifiées, après l'appel de `AcceptChanges`, les valeurs `Original` ne correspondront plus aux valeurs de la source de données.</span><span class="sxs-lookup"><span data-stu-id="4708b-147">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="4708b-148">`AcceptChanges` est appelé automatiquement pour chaque ligne au cours de l'appel de la méthode Update d'un `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="4708b-148">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="4708b-149">Vous pouvez conserver les valeurs d'origine au cours d'un appel de la méthode Update en commençant par affecter la valeur false à la propriété `AcceptChangesDuringUpdate` du `DataAdapter`, ou en créant un gestionnaire d'événements pour l'événement `RowUpdated` et en affectant la valeur <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> à <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="4708b-149">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="4708b-150">Pour plus d’informations, consultez [fusion du contenu des datasets](./dataset-datatable-dataview/merging-dataset-contents.md) et [gestion des événements DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="4708b-150">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="4708b-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="4708b-151">Example</span></span>

<span data-ttu-id="4708b-152">Les exemples suivants montrent comment effectuer des mises à jour vers des lignes modifiées en définissant explicitement le `UpdateCommand` d’un `DataAdapter` et en appelant sa `Update` méthode.</span><span class="sxs-lookup"><span data-stu-id="4708b-152">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="4708b-153">Notez que le paramètre spécifié dans la clause WHERE de l'instruction UPDATE est défini pour utiliser la valeur `Original` du `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="4708b-153">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="4708b-154">Cela est important car la valeur `Current` peut avoir été modifiée et ne pas correspondre à la valeur dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="4708b-154">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="4708b-155">La valeur `Original` est la valeur qui a été utilisée pour remplir le `DataTable` à partir de la source de données.</span><span class="sxs-lookup"><span data-stu-id="4708b-155">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="4708b-156">Colonnes AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="4708b-156">AutoIncrement Columns</span></span>

<span data-ttu-id="4708b-157">Si les tables de votre source de données ont des colonnes à incrémentation automatique, vous pouvez remplir les colonnes de votre `DataSet` soit en retournant la valeur d'auto-incrémentation comme paramètre de sortie d'une procédure stockée et en la mappant à une colonne dans une table, soit en utilisant l'événement `RowUpdated` du `DataAdapter` pour exécuter une instruction SELECT supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="4708b-157">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="4708b-158">Pour plus d’informations et pour obtenir un exemple, consultez [extraction des valeurs d’identité ou de numérotation NuméroAuto](retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="4708b-158">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="4708b-159">Ordre des insertions, mises à jour et suppressions</span><span class="sxs-lookup"><span data-stu-id="4708b-159">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="4708b-160">Dans de nombreuses circonstances, l'ordre dans lequel les modifications apportées dans le `DataSet` sont transmises à la source de données est important.</span><span class="sxs-lookup"><span data-stu-id="4708b-160">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="4708b-161">Par exemple, si une valeur de clé primaire d'une ligne existante est mise à jour et qu'une nouvelle ligne est ajoutée avec la nouvelle valeur de clé primaire en tant que clé primaire, il est important de traiter la mise à jour avant l'insertion.</span><span class="sxs-lookup"><span data-stu-id="4708b-161">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="4708b-162">Vous pouvez utiliser la méthode `Select` du `DataTable` pour retourner un tableau `DataRow` qui fait uniquement référence à des lignes ayant un `RowState` particulier.</span><span class="sxs-lookup"><span data-stu-id="4708b-162">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="4708b-163">Vous pouvez ensuite passer le tableau `DataRow` retourné à la méthode `Update` du `DataAdapter` pour traiter les lignes modifiées.</span><span class="sxs-lookup"><span data-stu-id="4708b-163">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="4708b-164">En spécifiant un sous-ensemble des lignes à mettre à jour, vous pouvez contrôler l'ordre dans lequel les insertions, mises à jour et suppressions sont traitées.</span><span class="sxs-lookup"><span data-stu-id="4708b-164">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="4708b-165">Exemple</span><span class="sxs-lookup"><span data-stu-id="4708b-165">Example</span></span>

<span data-ttu-id="4708b-166">Le code suivant garantit, par exemple, que seront d'abord traitées les lignes supprimées de la table puis les lignes mises à jour et enfin les lignes insérées.</span><span class="sxs-lookup"><span data-stu-id="4708b-166">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="4708b-167">Utiliser un DataAdapter pour récupérer et mettre à jour des données</span><span class="sxs-lookup"><span data-stu-id="4708b-167">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="4708b-168">Vous pouvez utiliser un DataAdapter pour récupérer et mettre à jour les données.</span><span class="sxs-lookup"><span data-stu-id="4708b-168">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="4708b-169">Cet exemple utilise DataAdapter.AcceptChangesDuringFill pour cloner les données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="4708b-169">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="4708b-170">Si la propriété a la valeur False, AcceptChanges n'est pas appelé lors du remplissage de la table, et les lignes récemment ajoutées sont traitées comme des lignes insérées.</span><span class="sxs-lookup"><span data-stu-id="4708b-170">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="4708b-171">Ainsi, l'exemple utilise ces lignes pour insérer de nouvelles lignes dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="4708b-171">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="4708b-172">Cet exemple utilise DataAdapter.TableMappings pour définir le mappage entre la table source et DataTable.</span><span class="sxs-lookup"><span data-stu-id="4708b-172">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="4708b-173">Cet exemple utilise DataAdapter.FillLoadOption pour déterminer comment l'adaptateur remplit DataTable à partir de DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="4708b-173">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="4708b-174">Lorsque vous créez un DataTable, vous pouvez uniquement écrire les données de la base de données dans la version actuelle ou la version d'origine en définissant la propriété comme LoadOption.Upsert ou LoadOption.PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="4708b-174">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="4708b-175">L'exemple met également à jour la table à l'aide de DbDataAdapter.UpdateBatchSize pour effectuer des opérations par lots.</span><span class="sxs-lookup"><span data-stu-id="4708b-175">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="4708b-176">Avant de compiler et d'exécuter l'exemple, vous devez créer l'exemple de base de données :</span><span class="sxs-lookup"><span data-stu-id="4708b-176">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
USE [master]
GO

CREATE DATABASE [MySchool]

GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)

SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

<span data-ttu-id="4708b-177">Vous trouverez des projets C# et Visual Basic avec cet exemple de code dans les [exemples de code pour développeurs](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="4708b-177">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="4708b-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4708b-178">See also</span></span>

- [<span data-ttu-id="4708b-179">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="4708b-179">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="4708b-180">États des lignes et versions des lignes</span><span class="sxs-lookup"><span data-stu-id="4708b-180">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="4708b-181">AcceptChanges et RejectChanges</span><span class="sxs-lookup"><span data-stu-id="4708b-181">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="4708b-182">Fusion de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="4708b-182">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="4708b-183">Récupération de valeurs d’identité ou de numérotation automatique</span><span class="sxs-lookup"><span data-stu-id="4708b-183">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="4708b-184">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4708b-184">ADO.NET Overview</span></span>](ado-net-overview.md)
