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
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a>TreeNodeCollection. Item lève une exception si le nœud est affecté ailleurs

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> lève une <xref:System.ArgumentException> si le nœud assigné est déjà lié à un autre <xref:System.Windows.Forms.TreeView> ou à ce à <xref:System.Windows.Forms.TreeView> un autre index.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, vous pouvez assigner un nœud d’arbre à une collection même s’il est déjà lié à un <xref:System.Windows.Forms.TreeView> . Cela peut entraîner des nœuds dupliqués. À compter de .NET 6,0, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> lève une <xref:System.ArgumentException> si le nœud assigné est déjà lié à un autre <xref:System.Windows.Forms.TreeView> ou à ce à <xref:System.Windows.Forms.TreeView> un index différent.

## <a name="reason-for-change"></a>Motif de modification

La validation du paramètre d’entrée est cohérente avec le comportement d’autres `TreeNodeCollection` API.

## <a name="version-introduced"></a>Version introduite

.NET 6,0 Preview 1

## <a name="recommended-action"></a>Action recommandée

Veillez à annuler la liaison d’un `TreeNode` avant de l’assigner à la collection.

## <a name="affected-apis"></a>API affectées

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
