---
title: Modification d’arborescences XML (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: 3402188c4e34ef81bad41ed49f9236b4fb7c47ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406883"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Modification d’arborescences XML (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est un magasin en mémoire pour une arborescence XML. Une fois que vous avez chargé ou analysé une arborescence XML à partir d’une source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permet de modifier cette arborescence sur place, puis de la sérialiser, par exemple en l’enregistrant dans un fichier ou en l’envoyant vers un serveur distant.  
  
 Lorsque vous modifiez une arborescence sur place, vous utilisez certaines méthodes, telles que <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Il existe cependant une autre approche, qui consiste à utiliser la construction fonctionnelle pour générer une nouvelle arborescence avec une forme différente. Cette approche peut s'avérer plus robuste et plus facile à développer, selon les types de modifications que vous devez apporter à votre arborescence XML et selon la taille de l'arborescence. La première rubrique dans cette section compare ces deux approches.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md)|Compare la modification d’une arborescence XML en mémoire à la construction fonctionnelle.|  
|[Ajout d’éléments, d’attributs et de nœuds à une arborescence XML (Visual Basic)](adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Fournit des informations sur l’ajout d’éléments, d’attributs ou de nœuds à une arborescence XML.|  
|[Modification d’éléments, d’attributs et de nœuds dans une arborescence XML](modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Fournit des informations sur la modification d'éléments, d'attributs ou de nœuds existants.|  
|[Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML (Visual Basic)](removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Fournit des informations sur la suppression d’éléments, d’attributs ou de nœuds d’une arborescence XML.|  
|[Gestion des paires nom/valeur (Visual Basic)](maintaining-name-value-pairs.md)|Décrit comment maintenir des informations d'applications qu'il est préférable de conserver sous la forme de paires nom/valeur, telles que des informations de configuration ou des paramètres globaux.|  
|[Procédure : modifier l’espace de noms pour une arborescence XML entière (Visual Basic)](how-to-change-the-namespace-for-an-entire-xml-tree.md)|Montre comment déplacer une arborescence XML d’un espace de noms à un autre.|  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)
