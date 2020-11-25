---
title: 'Modification avec rupture : les noms de paramètres ont été modifiés dans les assemblys de référence'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où certains noms de paramètres d’assembly de référence ont été modifiés pour correspondre aux noms de paramètres dans les assemblys d’implémentation.
ms.date: 11/01/2020
ms.openlocfilehash: c111428d0d7c103e01d725b21ff8d97d54ffeb33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760988"
---
# <a name="parameter-names-changed-in-reference-assemblies"></a><span data-ttu-id="6de88-103">Noms de paramètres modifiés dans les assemblys de référence</span><span class="sxs-lookup"><span data-stu-id="6de88-103">Parameter names changed in reference assemblies</span></span>

<span data-ttu-id="6de88-104">Certains noms de paramètres d’assembly de référence ont été modifiés pour correspondre aux noms de paramètres dans les assemblys d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="6de88-104">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

## <a name="change-description"></a><span data-ttu-id="6de88-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6de88-105">Change description</span></span>

<span data-ttu-id="6de88-106">Dans les versions précédentes de .NET, certains noms de paramètres d' [assembly de référence](../../../../standard/assembly/reference-assemblies.md) sont différents de leurs paramètres correspondants dans l’assembly d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="6de88-106">In previous .NET versions, some [reference assembly](../../../../standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="6de88-107">Cela peut provoquer des problèmes lors de l’utilisation d’arguments nommés et de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="6de88-107">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="6de88-108">Dans .NET 5,0, ces noms de paramètres incompatibles ont été mis à jour dans les assemblys de référence pour correspondre exactement aux noms de paramètres correspondants dans les assemblys d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="6de88-108">In .NET 5.0, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="6de88-109">Le tableau suivant indique les API et les noms de paramètres qui ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="6de88-109">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="6de88-110">API</span><span class="sxs-lookup"><span data-stu-id="6de88-110">API</span></span> | <span data-ttu-id="6de88-111">Ancien nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="6de88-111">Old parameter name</span></span> | <span data-ttu-id="6de88-112">Nouveau nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="6de88-112">New parameter name</span></span> |
| - | - | - |
| <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=nameWithType> | `stms` | `stmts` |
| <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=nameWithType> | `authType` | `authenticationType` |
| <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=nameWithType> | `o` | `obj` |
| <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=nameWithType> | `value` | `obj` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=nameWithType> | `value` | `strInput` |

## <a name="reason-for-change"></a><span data-ttu-id="6de88-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6de88-113">Reason for change</span></span>

<span data-ttu-id="6de88-114">Les noms de paramètres ont été modifiés pour des fins de cohérence et pour éviter des échecs lors de l’utilisation des arguments nommés et de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="6de88-114">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6de88-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6de88-115">Version introduced</span></span>

<span data-ttu-id="6de88-116">5.0</span><span class="sxs-lookup"><span data-stu-id="6de88-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6de88-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6de88-117">Recommended action</span></span>

<span data-ttu-id="6de88-118">Si vous rencontrez une erreur de compilation en raison d’un changement de nom de paramètre, mettez à jour le nom du paramètre en conséquence.</span><span class="sxs-lookup"><span data-stu-id="6de88-118">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6de88-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="6de88-119">Affected APIs</span></span>

- <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=fullName>
- <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)>
- <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=fullName>
- <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=fullName>
- <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Boolean)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Int32,System.Boolean)`
- `M:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)`
- `M:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})`
- `M:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String)`
- `M:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.Normalize(System.String)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)`
- `M:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)`
- `M:System.Drawing.Icon.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Drawing.Image.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`

-->
