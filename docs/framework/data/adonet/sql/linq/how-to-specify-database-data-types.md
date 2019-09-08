---
title: 'Procédure : Spécifier des types de données de base de données'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 09ca8dc6fa440138523bcd2905335a04517dd806
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793273"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="25fd7-102">Procédure : Spécifier des types de données de base de données</span><span class="sxs-lookup"><span data-stu-id="25fd7-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="25fd7-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> propriété sur un <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour spécifier le texte exact qui définit la colonne dans une déclaration de table T-SQL.</span><span class="sxs-lookup"><span data-stu-id="25fd7-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="25fd7-104">Vous devez spécifier la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> uniquement si vous envisagez d'utiliser <xref:System.Data.Linq.DataContext.CreateDatabase%2A> pour créer une instance de la base de données.</span><span class="sxs-lookup"><span data-stu-id="25fd7-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="25fd7-105">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="25fd7-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="25fd7-106">Pour spécifier du texte afin de définir un type de données dans une table T-SQL</span><span class="sxs-lookup"><span data-stu-id="25fd7-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="25fd7-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25fd7-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="25fd7-108">Affectez la valeur de la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> au texte exact utilisé par T-SQL.</span><span class="sxs-lookup"><span data-stu-id="25fd7-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25fd7-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25fd7-109">See also</span></span>

- [<span data-ttu-id="25fd7-110">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="25fd7-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="25fd7-111">Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="25fd7-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
