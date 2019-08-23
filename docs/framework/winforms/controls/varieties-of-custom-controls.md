---
title: Variétés de contrôles personnalisés
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
ms.openlocfilehash: 106da550fc6e6c50bc40e103e1f855059a9ffa9c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950092"
---
# <a name="varieties-of-custom-controls"></a>Variétés de contrôles personnalisés
.NET Framework vous offre la possibilité de développer et d’implémenter de nouveaux contrôles. Vous pouvez étendre les fonctionnalités du contrôle utilisateur standard et des contrôles existants grâce à l’héritage. Vous pouvez également créer des contrôles personnalisés qui gèrent eux-même leur apparence.  
  
 Le choix du type de contrôle à créer peut être délicat. Cette rubrique met en évidence les différences entre les nombreux types de contrôles à partir desquels vous pouvez hériter et vous guide dans le choix du type de contrôle adapté à votre projet.  
  
> [!NOTE]
> Pour plus d’informations sur la création d’un contrôle pour des Web Forms, consultez l’article [Développement de contrôles serveur ASP.NET personnalisés](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="base-control-class"></a>Classe de contrôle de base  
 La <xref:System.Windows.Forms.Control> classe est la classe de base pour les contrôles Windows Forms. Elle fournit l’infrastructure requise pour l’affichage dans les applications Windows Forms.  
  
 La <xref:System.Windows.Forms.Control> classe effectue les tâches suivantes pour fournir un affichage visuel dans Windows Forms applications:  
  
- Elle expose un handle de fenêtre.  
  
- Elle gère le routage des messages.  
  
- Elle fournit des événements de clavier et de souris, ainsi que de nombreux autres événements d’interface utilisateur.  
  
- Elle fournit des fonctionnalités de disposition avancées.  
  
- Contient de nombreuses propriétés spécifiques à l’affichage visuel, <xref:System.Windows.Forms.Control.ForeColor%2A>telles <xref:System.Windows.Forms.Control.BackColor%2A>que <xref:System.Windows.Forms.Control.Height%2A>,, <xref:System.Windows.Forms.Control.Width%2A>et.  
  
- Elle fournit la sécurité et la prise en charge des threads dont un contrôle Windows Forms a besoin pour se comporter comme un contrôle Microsoft® ActiveX®.  
  
 Étant donné que la majeure partie de l’infrastructure est fournie par la classe de base, il est relativement facile de développer vos propres contrôles Windows Forms.  
  
## <a name="kinds-of-controls"></a>Types de contrôles  
 Windows Forms prend en charge trois types de contrôles définis par l’utilisateur : *composite*, *étendu* et *personnalisé*. Les sections suivantes décrivent chaque type de contrôle et fournissent des recommandations pour choisir le type de contrôle à utiliser dans vos projets.  
  
### <a name="composite-controls"></a>Contrôles composites  
 Un contrôle composite est un ensemble de contrôles Windows Forms encapsulés dans un conteneur commun. Ce type de contrôle est parfois appelé *contrôle utilisateur*. Les contrôles contenus sont appelés *contrôles constitutifs*.  
  
 Un contrôle composite contient toutes les fonctionnalités inhérentes associées à chacun des contrôles Windows Forms contenus et vous permet d’exposer et de lier leurs propriétés de manière sélective. Un contrôle composite fournit également un grand nombre de fonctionnalités de gestion du clavier par défaut sans aucun effort de développement supplémentaire de votre part.  
  
 Un contrôle composite peut par exemple être conçu pour afficher des données d’adresses de clients à partir d’une base de données. Ce contrôle peut inclure un <xref:System.Windows.Forms.DataGridView> contrôle pour afficher les champs de base de <xref:System.Windows.Forms.BindingSource> données, un pour gérer la liaison à une source <xref:System.Windows.Forms.BindingNavigator> de données et un contrôle pour parcourir les enregistrements. Vous pourriez exposer de manière sélective les propriétés de liaison de données, mais aussi empaqueter et réutiliser l’ensemble du contrôle d’une application à l’autre. Pour obtenir un exemple de ce type de contrôle composite [, consultez Procédure: Appliquez des attributs dans les](how-to-apply-attributes-in-windows-forms-controls.md)contrôles Windows Forms.  
  
 Pour créer un contrôle composite, dérivez de la <xref:System.Windows.Forms.UserControl> classe. La <xref:System.Windows.Forms.UserControl> classe de base fournit le routage du clavier pour les contrôles enfants et permet aux contrôles enfants de fonctionner en tant que groupe. Pour plus d’informations, consultez l’article [Développement d’un contrôle Windows Forms composite](developing-a-composite-windows-forms-control.md).  
  
 **Recommendation**  
  
 Héritez de la classe <xref:System.Windows.Forms.UserControl> si :  
  
- vous souhaitez combiner les fonctionnalités de plusieurs contrôles Windows Forms dans une même entité réutilisable.  
  
### <a name="extended-controls"></a>Contrôles étendus  
 Vous pouvez dériver un contrôle hérité à partir de n'importe quel contrôle Windows Forms existant. Cette approche vous permet de conserver toutes les fonctionnalités inhérentes d’un contrôle Windows Forms et de les étendre en y ajoutant des propriétés et des méthodes personnalisées ou d’autres fonctionnalités. Avec cette option, vous pouvez remplacer la logique de peinture du contrôle de base, puis étendre son interface utilisateur en modifiant son apparence.  
  
 Par exemple, vous pouvez créer un contrôle dérivé <xref:System.Windows.Forms.Button> du contrôle qui effectue le suivi du nombre de fois qu’un utilisateur a cliqué dessus.  
  
 Dans certains contrôles, vous pouvez également ajouter une apparence personnalisée à l’interface utilisateur graphique de votre contrôle en substituant la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la classe de base. Pour un bouton étendu qui effectue le suivi des clics, vous pouvez <xref:System.Windows.Forms.Control.OnPaint%2A> substituer la méthode pour appeler l' <xref:System.Windows.Forms.Control.OnPaint%2A>implémentation de base de, puis dessiner le nombre de clics dans <xref:System.Windows.Forms.Button> un coin de la zone cliente du contrôle.  
  
 **Recommendation**  
  
 Héritez d'un contrôle Windows Forms si :  
  
- la plupart des fonctionnalités dont vous avez besoin sont déjà identiques à un contrôle Windows Forms existant ;  
  
- vous n’avez pas besoin d’une interface utilisateur graphique personnalisée ou vous souhaitez concevoir une nouvelle interface utilisateur graphique pour un contrôle existant.  
  
### <a name="custom-controls"></a>Contrôles personnalisés  
 Une autre façon de créer un contrôle consiste à en créer un sensiblement à partir du début en <xref:System.Windows.Forms.Control>héritant de. La <xref:System.Windows.Forms.Control> classe fournit toutes les fonctionnalités de base requises par les contrôles, notamment les événements de gestion de la souris et du clavier, mais pas les fonctionnalités spécifiques au contrôle ni l’interface graphique.  
  
 La création d’un contrôle en héritant <xref:System.Windows.Forms.Control> de la classe nécessite bien plus de réflexion et d’efforts <xref:System.Windows.Forms.UserControl> que l’héritage de ou d’un contrôle de Windows Forms existant. Comme vous gérez une grande partie de l’implémentation, votre contrôle peut avoir une plus grande flexibilité qu’un contrôle composite ou étendu, et vous pouvez personnaliser votre contrôle pour l’adapter à vos besoins spécifiques.  
  
 Pour implémenter un contrôle personnalisé, vous devez écrire du code <xref:System.Windows.Forms.Control.OnPaint%2A> pour l’événement du contrôle, ainsi que tout code spécifique aux fonctionnalités dont vous avez besoin. Vous pouvez également remplacer la méthode <xref:System.Windows.Forms.Control.WndProc%2A> et gérer les messages Windows directement. Il s’agit de la façon la plus efficace pour créer un contrôle, à condition de bien connaître l’API Microsoft Win32®.  
  
 Un contrôle personnalisé peut par exemple être un contrôle d’horloge imitant l’apparence et le comportement d’une horloge analogique. La peinture personnalisée est appelée pour provoquer le déplacement des mains de l’horloge en réponse aux <xref:System.Windows.Forms.Timer.Tick> événements d’un composant <xref:System.Windows.Forms.Timer> interne. Pour plus d'informations, voir [Procédure : Développez un contrôle](how-to-develop-a-simple-windows-forms-control.md)de Windows Forms simple.  
  
 **Recommendation**  
  
 Héritez de la classe <xref:System.Windows.Forms.Control> si :  
  
- vous souhaitez fournir une représentation graphique personnalisée de votre contrôle ;  
  
- vous devez implémenter des fonctionnalités personnalisées qui ne sont pas disponible via les contrôles standard.  
  
### <a name="activex-controls"></a>Contrôles ActiveX  
 Même si l’infrastructure Windows Forms a été optimisée pour héberger des contrôles Windows Forms, vous pouvez tout de même utiliser des contrôles ActiveX. Cette tâche est prise en charge dans Visual Studio. Pour plus d'informations, voir [Procédure : Ajoutez des contrôles ActiveX à](how-to-add-activex-controls-to-windows-forms.md)Windows Forms.  
  
### <a name="windowless-controls"></a>Contrôles sans fenêtre  
 Les technologies Microsoft Visual Basic® 6.0 et ActiveX prennent en charge les contrôles *sans fenêtre*. Les contrôles sans fenêtre ne sont pas pris en charge dans les Windows Forms.  
  
## <a name="custom-design-experience"></a>Conception personnalisée  
 Si vous devez implémenter une expérience de conception personnalisée, vous pouvez créer votre propre concepteur. Pour les contrôles composites, dérivez votre classe <xref:System.Windows.Forms.Design.ParentControlDesigner> de concepteur <xref:System.Windows.Forms.Design.DocumentDesigner> personnalisée à partir des classes ou. Pour les contrôles étendus et personnalisés, dérivez votre classe <xref:System.Windows.Forms.Design.ControlDesigner> de concepteur personnalisée de la classe.  
  
 <xref:System.ComponentModel.DesignerAttribute> Utilisez pour associer votre contrôle à votre concepteur. Pour plus d’informations, consultez extension de la [prise en charge au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) et [procédure: Créez un contrôle de Windows Forms qui tire parti des fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))au moment du Design.  
  
## <a name="see-also"></a>Voir aussi

- [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
- [Guide pratique pour Développer un contrôle de Windows Forms simple](how-to-develop-a-simple-windows-forms-control.md)
- [Développement d’un contrôle Windows Forms composite](developing-a-composite-windows-forms-control.md)
- [Extension de la prise en charge au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Guide pratique : Créer un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
