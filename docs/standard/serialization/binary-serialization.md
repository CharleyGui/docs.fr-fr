---
title: Sérialisation binaire
description: Cet article décrit la sérialisation binaire et les types pour lesquels .NET Core le prend en charge. Tenez compte des dangers de la sérialisation binaire et des alternatives à celle-ci.
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 4ed76437b743da842d6ba07d29fe7985f824abf0
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421278"
---
# <a name="binary-serialization"></a><span data-ttu-id="84711-104">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="84711-104">Binary serialization</span></span>

<span data-ttu-id="84711-105">La sérialisation peut être définie comme le processus de stockage de l'état d'un objet sur un support de stockage.</span><span class="sxs-lookup"><span data-stu-id="84711-105">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="84711-106">Pendant ce processus, les champs publics et privés de l'objet et le nom de la classe, y compris l'assembly contenant la classe, sont convertis en un flux de données d'octets, écrit ensuite dans un flux de données.</span><span class="sxs-lookup"><span data-stu-id="84711-106">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="84711-107">Lorsque l'objet est désérialisé par la suite, un clone exact de l'objet d'origine est créé.</span><span class="sxs-lookup"><span data-stu-id="84711-107">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="84711-108">Lorsque vous implémentez un mécanisme de sérialisation dans un environnement orienté objet, vous devez faire plusieurs compromis entre facilité d'utilisation et souplesse.</span><span class="sxs-lookup"><span data-stu-id="84711-108">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="84711-109">Le processus peut être automatisé en grande partie, à condition que vous puissiez suffisamment le contrôler.</span><span class="sxs-lookup"><span data-stu-id="84711-109">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="84711-110">Par exemple, dans certaines situations, la sérialisation binaire simple n'est pas suffisante ou une raison particulière peut exiger la définition des champs à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="84711-110">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="84711-111">Les sections suivantes étudient le mécanisme de sérialisation fiable fourni avec .NET et mettent en évidence plusieurs fonctionnalités importantes qui vous permettent de personnaliser le processus en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="84711-111">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="84711-112">L'état d'un objet encodé UTF-8 ou UTF-7 n'est pas préservé si l'objet est sérialisé et désérialisé à l'aide de différentes versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84711-112">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="84711-113">La sérialisation binaire permet de modifier les membres privés à l’intérieur d’un objet et par conséquent de modifier l’état de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="84711-113">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="84711-114">Pour cette raison, d’autres infrastructures de sérialisation, comme <xref:System.Text.Json?displayProperty=fullName> , qui opèrent sur la surface de l’API publique sont recommandées.</span><span class="sxs-lookup"><span data-stu-id="84711-114">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="84711-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="84711-115">.NET Core</span></span>

<span data-ttu-id="84711-116">.NET Core prend en charge la sérialisation binaire pour un sous-ensemble de types.</span><span class="sxs-lookup"><span data-stu-id="84711-116">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="84711-117">Vous pouvez voir la liste des types pris en charge dans la section [types sérialisables](#serializable-types) qui suit.</span><span class="sxs-lookup"><span data-stu-id="84711-117">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="84711-118">Les types répertoriés sont garantis comme étant sérialisables entre .NET Framework 4.5.1 et les versions ultérieures et entre .NET Core 2,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="84711-118">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="84711-119">D’autres implémentations de .NET, telles que mono, ne sont pas officiellement prises en charge, mais doivent également fonctionner.</span><span class="sxs-lookup"><span data-stu-id="84711-119">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="84711-120">Types sérialisables</span><span class="sxs-lookup"><span data-stu-id="84711-120">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="84711-121">Type</span><span class="sxs-lookup"><span data-stu-id="84711-121">Type</span></span> | <span data-ttu-id="84711-122">Notes</span><span class="sxs-lookup"><span data-stu-id="84711-122">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="84711-123">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="84711-124">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="84711-125">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="84711-126">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="84711-127">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="84711-128">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="84711-129">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="84711-130">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="84711-131">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="84711-132">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="84711-133">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="84711-134">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="84711-135">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-136">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="84711-137">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="84711-138">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="84711-139">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="84711-140">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-140">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="84711-141">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-141">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="84711-142">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-142">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="84711-143">La sérialisation de .NET Framework à .NET Core n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="84711-143">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="84711-144">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="84711-145">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="84711-146">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="84711-147">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="84711-148">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="84711-149">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-150">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="84711-151">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-151">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="84711-152">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="84711-153">À compter de .NET Core 2.0.2 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="84711-153">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="84711-154">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="84711-155">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="84711-156">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-156">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="84711-157">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="84711-158">Si vous définissez `RemotingFormat` sur `SerializationFormat.Binary` , il ne peut être échangé qu’avec .net Core 2,1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="84711-158">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="84711-159">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="84711-160">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="84711-161">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="84711-162">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="84711-163">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="84711-164">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="84711-165">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="84711-166">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="84711-167">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="84711-168">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="84711-169">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-169">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="84711-170">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-170">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="84711-171">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-171">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="84711-172">La sérialisation de .NET Framework à .NET Core n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="84711-172">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="84711-173">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="84711-174">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="84711-175">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="84711-176">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="84711-177">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="84711-178">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="84711-179">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-180">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="84711-181">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="84711-182">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="84711-183">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-184">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="84711-185">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="84711-186">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="84711-187">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="84711-188">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="84711-189">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="84711-190">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="84711-191">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="84711-192">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-193">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="84711-194">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="84711-195">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="84711-196">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="84711-197">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="84711-198">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="84711-199">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="84711-200">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="84711-201">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="84711-202">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="84711-203">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="84711-204">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-205">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="84711-206">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-206">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-207">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="84711-208">À partir de .NET Core 2.0.6.</span><span class="sxs-lookup"><span data-stu-id="84711-208">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="84711-209">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="84711-210">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="84711-211">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-212">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="84711-213">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-214">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="84711-215">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="84711-216">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="84711-217">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-218">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="84711-219">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="84711-220">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="84711-221">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="84711-222">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="84711-223">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="84711-224">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="84711-225">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="84711-226">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="84711-227">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="84711-228">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="84711-229">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="84711-230">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="84711-231">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="84711-232">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="84711-233">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="84711-234">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="84711-235">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="84711-236">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="84711-237">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="84711-238">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="84711-239">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="84711-240">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="84711-241">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="84711-242">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="84711-243">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="84711-244">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="84711-245">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="84711-246">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="84711-247">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="84711-248">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="84711-249">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="84711-250">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="84711-251">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="84711-252">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="84711-253">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="84711-254">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="84711-255">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="84711-256">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="84711-257">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="84711-258">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="84711-259">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-259">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="84711-260">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-260">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="84711-261">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-261">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="84711-262">La sérialisation de .NET Framework à .NET Core n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="84711-262">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="84711-263">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="84711-264">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="84711-265">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="84711-266">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="84711-267">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="84711-268">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="84711-269">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="84711-270">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="84711-271">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="84711-272">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="84711-273">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="84711-274">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="84711-275">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="84711-276">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="84711-277">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="84711-278">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="84711-279">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="84711-280">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="84711-281">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-281">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="84711-282">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="84711-283">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-283">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="84711-284">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="84711-285">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="84711-286">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-286">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="84711-287">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-287">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="84711-288">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-288">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="84711-289">Données de sérialisation limitées.</span><span class="sxs-lookup"><span data-stu-id="84711-289">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="84711-290">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="84711-291">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="84711-292">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="84711-293">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="84711-294">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="84711-295">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="84711-296">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="84711-297">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="84711-298">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="84711-299">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="84711-300">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="84711-301">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="84711-302">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="84711-303">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="84711-304">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="84711-305">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="84711-306">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="84711-307">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="84711-308">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="84711-309">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="84711-310">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="84711-311">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="84711-312">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="84711-313">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="84711-314">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="84711-315">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="84711-316">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="84711-317">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="84711-318">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="84711-319">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="84711-320">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="84711-321">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-321">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="84711-322">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="84711-323">Non sérialisable dans .NET Framework 4,7 et versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="84711-323">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="84711-324">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="84711-325">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="84711-326">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="84711-327">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="84711-328">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-328">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="84711-329">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-329">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="84711-330">À partir de .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="84711-330">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="84711-331">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84711-331">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="84711-332">Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.</span><span class="sxs-lookup"><span data-stu-id="84711-332">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="84711-333">[Sérialisation XML et SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="84711-333">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="84711-334">Décrit le mécanisme de sérialisation XML inclus avec le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="84711-334">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="84711-335">[Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="84711-335">[Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="84711-336">Décrit les indications de codage sécurisé à suivre lors de l'écriture du code qui exécute la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="84711-336">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="84711-337">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="84711-337">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="84711-338">Décrit les différentes méthodes à partir de .NET Framework pour les communications à distance.</span><span class="sxs-lookup"><span data-stu-id="84711-338">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="84711-339">[Services Web XML créés à l’aide des clients de service Web XML et ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="84711-339">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="84711-340">Articles qui décrivent et expliquent comment programmer des services Web XML créés à l’aide de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="84711-340">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
