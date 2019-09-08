---
title: 'Procédure : Personnaliser les flux avec le fournisseur de Entity Framework (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 8f994065ea42d6fc522fa297cafa8c46a8164e67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780151"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Procédure : Personnaliser les flux avec le fournisseur de Entity Framework (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de personnaliser la sérialisation Atom dans une réponse du service de données pour pouvoir mapper les propriétés d'une entité aux éléments inutilisés définis dans le protocole AtomPub. Cette rubrique montre comment définir des attributs de mappage pour les types d’entité dans un modèle de données défini dans un fichier .edmx à l’aide du fournisseur Entity Framework. Pour plus d’informations, consultez [Personnalisation des flux](feed-customization-wcf-data-services.md).  
  
 Dans cette rubrique vous modifierez manuellement le fichier .edmx généré par un outil qui contient le modèle de données. Vous devez modifier manuellement le fichier car les extensions vers le modèle de données ne sont pas prises en charge par le Concepteur d'entités. Pour plus d’informations sur le fichier. edmx généré par les outils de Entity Data Model, consultez [vue d’ensemble du fichier. edmx (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Pour modifier manuellement le fichier Northwind.edmx pour ajouter des attributs de personnalisation de flux  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton `Northwind.edmx` droit sur le fichier, puis cliquez sur **Ouvrir avec**.  
  
2. Dans la boîte de dialogue **Ouvrir avec-Northwind. edmx** , sélectionnez **éditeur XML**, puis cliquez sur **OK**.  
  
3. Localisez l'élément `ConceptualModels` et remplacez le type d'entité `Customers` existant par l'élément suivant qui contient des attributs de mappage de personnalisation de flux :  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. Enregistrez les modifications et fermez le fichier Northwind.edmx.  
  
5. Facultatif Cliquez avec le bouton droit sur le fichier Northwind. edmx, puis cliquez sur **exécuter un outil personnalisé**.  
  
     Cette opération régénère le fichier de couche objet qui peut être obligatoire.  
  
6. Recompilez le projet.  
  
## <a name="example"></a>Exemple  
 L'exemple précédent retourne le résultat suivant pour l'URI `http://myservice/Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseur Entity Framework](entity-framework-provider-wcf-data-services.md)
