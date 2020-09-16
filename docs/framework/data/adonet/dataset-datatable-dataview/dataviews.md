---
title: DataViews
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: fe6adac35c157b454f5e33d3526196d4f408fd89
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546866"
---
# <a name="dataviews"></a>DataViews
Un objet <xref:System.Data.DataView> vous permet de créer différentes vues des données stockées dans un objet <xref:System.Data.DataTable>, possibilité qui est souvent utilisée dans les applications de liaison de données. À l’aide d’un **DataView**, vous pouvez exposer les données d’une table avec différents ordres de tri, et vous pouvez filtrer les données par État de ligne ou en fonction d’une expression de filtre.

 Un **DataView** fournit une vue dynamique des données dans le **DataTable**sous-jacent : le contenu, le classement et l’appartenance reflètent les modifications à mesure qu’elles se produisent. Ce comportement diffère de la méthode **Select** du **DataTable**, qui retourne un <xref:System.Data.DataRow> tableau à partir d’une table en fonction d’un filtre et/ou d’un ordre de tri particulier : ce contenu reflète les modifications apportées à la table sous-jacente, mais son appartenance et son ordre restent statiques. Les fonctionnalités dynamiques du **DataView** la rendent idéale pour les applications de liaison de données.

 Un **DataView** vous offre une vue dynamique d’un seul jeu de données, comme une vue de base de données, à laquelle vous pouvez appliquer différents critères de tri et de filtrage. Toutefois, contrairement à une vue de base de données, un **DataView** ne peut pas être traité comme une table et ne peut pas fournir une vue des tables jointes. Vous ne pouvez pas non plus exclure des colonnes qui existent dans la table source ou des colonnes Append qui n’existent pas dans la table source, telles que les colonnes de calcul.

 Vous pouvez utiliser un <xref:System.Data.DataView.DataViewManager%2A> pour gérer les paramètres de vue pour toutes les tables d’un **DataSet**. Le **DataViewManager** vous offre un moyen pratique de gérer les paramètres d’affichage par défaut pour chaque table. Lors de la liaison d’un contrôle à plusieurs tables d’un **DataSet**, la liaison à un **DataViewManager** est le choix idéal.

## <a name="in-this-section"></a>Dans cette section
 [Création d’un DataView](creating-a-dataview.md) Décrit comment créer un **DataView** pour un **DataTable**.

 [Tri et filtrage des données](sorting-and-filtering-data.md) Décrit comment définir les propriétés d’un **DataView** pour retourner des sous-ensembles de lignes de données répondant à des critères de filtre spécifiques ou pour retourner des données dans un ordre de tri particulier.

 [DataRows et DataRowViews](datarows-and-datarowviews.md) Décrit comment accéder aux données exposées par le **DataView**.

 [Recherche de lignes](finding-rows.md) Décrit comment rechercher une ligne particulière dans un **DataView**.

 [ChildView et relations](childviews-and-relations.md) Décrit comment créer des vues de données à partir d’une relation parent-enfant à l’aide d’un **DataView**.

 [Modification des DataView](modifying-dataviews.md) Décrit comment modifier les données du **DataTable** sous-jacent par le biais du **DataView**, y compris l’activation ou la désactivation des mises à jour.

 [Gestion des événements DataView](handling-dataview-events.md) Décrit comment utiliser l’événement **ListChanged** pour recevoir une notification lors de la mise à jour du contenu ou de l’ordre d’un **DataView** .

 [Gestion des DataView](managing-dataviews.md) Décrit comment utiliser un **DataViewManager** pour gérer les paramètres **DataView** pour chaque table d’un **DataSet**.

## <a name="related-sections"></a>Sections connexes
 [Applications Web ASP.net](/previous-versions/655cec97(v=vs.100)) Fournit des vues d’ensemble et des procédures pas à pas détaillées pour la création d’applications ASP.NET, de Web Forms et de services Web.

 [Applications Windows](/previous-versions/ms184421(v=vs.100)) Fournit des informations détaillées sur l’utilisation des Windows Forms et des applications console.

 [Jeux de données, DataTables et DataView](index.md) Décrit l’objet **DataSet** et comment vous pouvez l’utiliser pour gérer les données d’application.

 [DataTables](datatables.md) Décrit l’objet **DataTable** et comment vous pouvez l’utiliser pour gérer des données d’application en soi ou dans le cadre d’un **DataSet**.

 [ADO.net](../index.md) Décrit l’architecture et les composants ADO.NET et comment utiliser ADO.NET pour accéder à des sources de données existantes et gérer des données d’application.

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
