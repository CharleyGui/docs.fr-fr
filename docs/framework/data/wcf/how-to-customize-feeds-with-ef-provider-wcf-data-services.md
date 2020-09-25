---
title: 'Comment : personnaliser les flux avec le fournisseur Entity Framework (services de données WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 76cc8da052ee51157857418cd81088a523f95ea2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186589"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Comment : personnaliser les flux avec le fournisseur Entity Framework (services de données WCF)

WCF Data Services vous permet de personnaliser la sérialisation Atom dans une réponse du service de données afin que les propriétés d’une entité puissent être mappées aux éléments inutilisés définis dans le protocole AtomPub. Cette rubrique montre comment définir des attributs de mappage pour les types d’entité dans un modèle de données défini dans un fichier .edmx à l’aide du fournisseur Entity Framework. Pour plus d’informations, consultez [Personnalisation des flux](feed-customization-wcf-data-services.md).  
  
 Dans cette rubrique vous modifierez manuellement le fichier .edmx généré par un outil qui contient le modèle de données. Vous devez modifier manuellement le fichier car les extensions vers le modèle de données ne sont pas prises en charge par le Concepteur d'entités. Pour plus d’informations sur le fichier. edmx généré par les outils de Entity Data Model, consultez [vue d’ensemble du fichier. edmx (Entity Framework)](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Pour modifier manuellement le fichier Northwind.edmx pour ajouter des attributs de personnalisation de flux  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `Northwind.edmx` fichier, puis cliquez sur **Ouvrir avec**.  
  
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
