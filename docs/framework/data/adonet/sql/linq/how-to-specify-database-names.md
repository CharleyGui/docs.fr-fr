---
title: 'Procédure : Spécifier des noms de bases de données'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 0daf754edf624410e0ea725acd6c266ccb7828dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781579"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="ed405-102">Procédure : Spécifier des noms de bases de données</span><span class="sxs-lookup"><span data-stu-id="ed405-102">How to: Specify Database Names</span></span>
<span data-ttu-id="ed405-103">Utilisez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> sur un attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> pour spécifier le nom d'une base de données lorsque la connexion ne fournit pas de nom.</span><span class="sxs-lookup"><span data-stu-id="ed405-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="ed405-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed405-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="ed405-105">Pour spécifier le nom de la base de données</span><span class="sxs-lookup"><span data-stu-id="ed405-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="ed405-106">Ajoutez l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> à la déclaration de classe de la base de données.</span><span class="sxs-lookup"><span data-stu-id="ed405-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="ed405-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> à l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ed405-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="ed405-108">Affectez le nom que vous souhaitez spécifier à la valeur de propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed405-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed405-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed405-109">See also</span></span>

- [<span data-ttu-id="ed405-110">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ed405-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ed405-111">Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="ed405-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
