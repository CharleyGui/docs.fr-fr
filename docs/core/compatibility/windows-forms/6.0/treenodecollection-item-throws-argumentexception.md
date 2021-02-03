---
title: 'Modification avec rupture : TreeNodeCollection. Item (Int32) lève une exception ArgumentException pour le nœud en cours d’utilisation'
description: En savoir plus sur la modification avec rupture dans .NET 6,0 où TreeNodeCollection. Item (Int32) lève désormais une exception ArgumentException si le nœud assigné est déjà affecté à un TreeView.
ms.date: 01/19/2021
ms.openlocfilehash: efd6ca5d594b2aa64e10cce2cef6c0e1c411bb1e
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506575"
---
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a><span data-ttu-id="df070-103">TreeNodeCollection. Item lève une exception si le nœud est affecté ailleurs</span><span class="sxs-lookup"><span data-stu-id="df070-103">TreeNodeCollection.Item throws exception if node is assigned elsewhere</span></span>

<span data-ttu-id="df070-104"><xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> lève une <xref:System.ArgumentException> si le nœud assigné est déjà lié à un autre <xref:System.Windows.Forms.TreeView> ou à ce à <xref:System.Windows.Forms.TreeView> un autre index.</span><span class="sxs-lookup"><span data-stu-id="df070-104"><xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> throws an <xref:System.ArgumentException> if the node being assigned is already bound to another <xref:System.Windows.Forms.TreeView> or to this <xref:System.Windows.Forms.TreeView> at a different index.</span></span>

## <a name="change-description"></a><span data-ttu-id="df070-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="df070-105">Change description</span></span>

<span data-ttu-id="df070-106">Dans les versions précédentes de .NET, vous pouvez assigner un nœud d’arbre à une collection même s’il est déjà lié à un <xref:System.Windows.Forms.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="df070-106">In previous .NET versions, you can assign a tree node to a collection even if it's already bound to a <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="df070-107">Cela peut entraîner des nœuds dupliqués.</span><span class="sxs-lookup"><span data-stu-id="df070-107">This can lead to duplicated nodes.</span></span> <span data-ttu-id="df070-108">À compter de .NET 6,0, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> lève une <xref:System.ArgumentException> si le nœud assigné est déjà lié à un autre <xref:System.Windows.Forms.TreeView> ou à ce à <xref:System.Windows.Forms.TreeView> un index différent.</span><span class="sxs-lookup"><span data-stu-id="df070-108">Starting in .NET 6.0, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> throws an <xref:System.ArgumentException> if the node being assigned is already bound to another <xref:System.Windows.Forms.TreeView> or to this <xref:System.Windows.Forms.TreeView> at a different index.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="df070-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="df070-109">Reason for change</span></span>

<span data-ttu-id="df070-110">La validation du paramètre d’entrée est cohérente avec le comportement d’autres `TreeNodeCollection` API.</span><span class="sxs-lookup"><span data-stu-id="df070-110">Validating the input parameter is consistent with the behavior of other `TreeNodeCollection` APIs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="df070-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="df070-111">Version introduced</span></span>

<span data-ttu-id="df070-112">.NET 6,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="df070-112">.NET 6.0 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="df070-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="df070-113">Recommended action</span></span>

<span data-ttu-id="df070-114">Veillez à annuler la liaison d’un `TreeNode` avant de l’assigner à la collection.</span><span class="sxs-lookup"><span data-stu-id="df070-114">Make sure to unbind a `TreeNode` before assigning it to the collection.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="df070-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="df070-115">Affected APIs</span></span>

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
