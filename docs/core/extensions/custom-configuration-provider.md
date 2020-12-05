---
title: Implémenter un fournisseur de configuration personnalisé dans .NET
description: Découvrez comment implémenter un fournisseur de configuration personnalisé dans des applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.topic: how-to
ms.openlocfilehash: 22e46b7df8b02421633d6be251d990879baa8b2b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740116"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a><span data-ttu-id="7eac2-103">Implémenter un fournisseur de configuration personnalisé dans .NET</span><span class="sxs-lookup"><span data-stu-id="7eac2-103">Implement a custom configuration provider in .NET</span></span>

<span data-ttu-id="7eac2-104">De nombreux [fournisseurs de configuration](configuration-providers.md) sont disponibles pour les sources de configuration courantes, telles que les fichiers JSON, XML et ini.</span><span class="sxs-lookup"><span data-stu-id="7eac2-104">There are many [configuration providers](configuration-providers.md) available for common configuration sources such as JSON, XML, and INI files.</span></span> <span data-ttu-id="7eac2-105">Vous devrez peut-être implémenter un fournisseur de configuration personnalisé lorsque l’un des fournisseurs disponibles ne répond pas aux besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="7eac2-105">You may need to implement a custom configuration provider when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="7eac2-106">Dans cet article, vous allez apprendre à implémenter un fournisseur de configuration personnalisé qui s’appuie sur une base de données comme source de configuration.</span><span class="sxs-lookup"><span data-stu-id="7eac2-106">In this article, you'll learn how to implement a custom configuration provider that relies on a database as its configuration source.</span></span>

## <a name="custom-configuration-provider"></a><span data-ttu-id="7eac2-107">Fournisseur de configuration personnalisé</span><span class="sxs-lookup"><span data-stu-id="7eac2-107">Custom configuration provider</span></span>

<span data-ttu-id="7eac2-108">L’exemple d’application montre comment créer un fournisseur de configuration de base qui lit les paires clé-valeur de configuration à partir d’une base de données à l’aide d' [Entity Framework (EF) Core](/ef/core).</span><span class="sxs-lookup"><span data-stu-id="7eac2-108">The sample app demonstrates how to create a basic configuration provider that reads configuration key-value pairs from a database using [Entity Framework (EF) Core](/ef/core).</span></span>

<span data-ttu-id="7eac2-109">Le fournisseur présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="7eac2-109">The provider has the following characteristics:</span></span>

- <span data-ttu-id="7eac2-110">La base de données en mémoire EF est utilisée à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="7eac2-110">The EF in-memory database is used for demonstration purposes.</span></span> <span data-ttu-id="7eac2-111">Pour utiliser une base de données qui nécessite une chaîne de connexion, implémentez un autre `ConfigurationBuilder` pour fournir la chaîne de connexion à partir d’un autre fournisseur de configuration.</span><span class="sxs-lookup"><span data-stu-id="7eac2-111">To use a database that requires a connection string, implement a secondary `ConfigurationBuilder` to supply the connection string from another configuration provider.</span></span>
- <span data-ttu-id="7eac2-112">Le fournisseur lit une table de base de données dans la configuration au démarrage.</span><span class="sxs-lookup"><span data-stu-id="7eac2-112">The provider reads a database table into configuration at startup.</span></span> <span data-ttu-id="7eac2-113">Le fournisseur n’interroge pas la base de données par clé.</span><span class="sxs-lookup"><span data-stu-id="7eac2-113">The provider doesn't query the database on a per-key basis.</span></span>
- <span data-ttu-id="7eac2-114">Le rechargement en cas de changement n’est pas implémenté, par conséquent, la mise à jour la base de données après le démarrage de l’application n’a aucun effet sur la configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="7eac2-114">Reload-on-change isn't implemented, so updating the database after the app starts has no effect on the app's configuration.</span></span>

<span data-ttu-id="7eac2-115">Définissez une `Settings` entité de type d’enregistrement pour le stockage des valeurs de configuration dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="7eac2-115">Define a `Settings` record type entity for storing configuration values in the database.</span></span> <span data-ttu-id="7eac2-116">Par exemple, vous pouvez ajouter un fichier *Settings.cs* dans votre dossier de *modèles* :</span><span class="sxs-lookup"><span data-stu-id="7eac2-116">For example, you could add a *Settings.cs* file in your *Models* folder:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

<span data-ttu-id="7eac2-117">Pour plus d’informations sur les types d’enregistrements, consultez [types d’enregistrements en C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="7eac2-117">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="7eac2-118">Ajoutez un `EntityConfigurationContext` pour stocker les valeurs configurées et y accéder.</span><span class="sxs-lookup"><span data-stu-id="7eac2-118">Add an `EntityConfigurationContext` to store and access the configured values.</span></span>

<span data-ttu-id="7eac2-119">*Fournisseurs/EntityConfigurationContext. cs*:</span><span class="sxs-lookup"><span data-stu-id="7eac2-119">*Providers/EntityConfigurationContext.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<span data-ttu-id="7eac2-120">Créez une classe qui implémente <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span><span class="sxs-lookup"><span data-stu-id="7eac2-120">Create a class that implements <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span></span>

<span data-ttu-id="7eac2-121">*Fournisseurs/EntityConfigurationSource. cs*:</span><span class="sxs-lookup"><span data-stu-id="7eac2-121">*Providers/EntityConfigurationSource.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<span data-ttu-id="7eac2-122">Créez le fournisseur de configuration personnalisé en héritant de <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span><span class="sxs-lookup"><span data-stu-id="7eac2-122">Create the custom configuration provider by inheriting from <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span></span> <span data-ttu-id="7eac2-123">Le fournisseur de configuration initialise la base de données quand elle est vide.</span><span class="sxs-lookup"><span data-stu-id="7eac2-123">The configuration provider initializes the database when it's empty.</span></span> <span data-ttu-id="7eac2-124">Étant donné que les clés de configuration ne respectent pas la casse, le dictionnaire utilisé pour initialiser la base de données est créé avec le comparateur ne respectant pas la casse ([StringComparer. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span><span class="sxs-lookup"><span data-stu-id="7eac2-124">Since configuration keys are case-insensitive, the dictionary used to initialize the database is created with the case-insensitive comparer ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span></span>

<span data-ttu-id="7eac2-125">*Fournisseurs/EntityConfigurationProvider. cs*:</span><span class="sxs-lookup"><span data-stu-id="7eac2-125">*Providers/EntityConfigurationProvider.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

<span data-ttu-id="7eac2-126">Une `AddEntityConfiguration` méthode d’extension autorise l’ajout de la source de configuration à une <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span><span class="sxs-lookup"><span data-stu-id="7eac2-126">An `AddEntityConfiguration` extension method permits adding the configuration source to a <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span></span>

<span data-ttu-id="7eac2-127">*Extensions/ConfigurationBuilderExtensions. cs*:</span><span class="sxs-lookup"><span data-stu-id="7eac2-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

<span data-ttu-id="7eac2-128">Le code suivant montre comment utiliser le `EntityConfigurationProvider` personnalisé dans *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="7eac2-128">The following code shows how to use the custom `EntityConfigurationProvider` in *Program.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="27-28":::

## <a name="see-also"></a><span data-ttu-id="7eac2-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eac2-129">See also</span></span>

- [<span data-ttu-id="7eac2-130">Configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="7eac2-130">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="7eac2-131">Fournisseurs de configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="7eac2-131">Configuration providers in .NET</span></span>](configuration-providers.md)
