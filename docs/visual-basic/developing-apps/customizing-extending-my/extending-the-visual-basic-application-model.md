---
title: Extension du modèle d'application Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 46c18ab540c90c4147514685c2acc824755b435f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976860"
---
# <a name="extending-the-visual-basic-application-model"></a>Extension du modèle d'application Visual Basic

Vous pouvez ajouter des fonctionnalités au modèle d’application en substituant `Overridable` les membres de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> la classe. Cette technique vous permet de personnaliser le comportement du modèle d’application et d’ajouter des appels à vos propres méthodes au démarrage et à l’arrêt de l’application.

## <a name="visual-overview-of-the-application-model"></a>Vue d’ensemble visuelle du modèle d’application

Cette section présente visuellement la séquence d’appels de fonction dans le modèle d’application Visual Basic. La section suivante décrit l’objectif de chaque fonction en détail.

Le graphique suivant montre la séquence d’appel du modèle d’application dans une application Visual Basic Windows Forms normale. La séquence démarre lorsque la `Sub Main` procédure appelle la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> méthode.

![Diagramme montrant la séquence d’appel du modèle d’application.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Le modèle d’application Visual Basic fournit également <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> les <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> événements et. Les graphiques suivants montrent le mécanisme permettant de déclencher ces événements.

![Diagramme montrant la méthode OnStartupNextInstance déclenchant l’événement StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![Diagramme montrant la méthode OnUnhandledException déclenchant l’événement UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Substitution des méthodes de base

La <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> méthode définit l’ordre dans lequel les `Application` méthodes sont exécutées. Par défaut, la `Sub Main` procédure d’une application Windows Forms appelle la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> méthode.

Si l’application est une application normale (application à instances multiples) ou la première instance d’une application à instance unique, la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> méthode exécute les `Overridable` méthodes dans l’ordre suivant :

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Par défaut, cette méthode définit les styles visuels, les styles d’affichage du texte et le principal actuel du thread d’application principal (si l’application utilise l’authentification Windows `ShowSplashScreen` ) et `/nosplash` appelle `-nosplash` si ni ni n’est utilisé comme argument de ligne de commande.

     La séquence de démarrage de l’application est annulée si `False`cette fonction retourne. Cela peut être utile dans certains cas où l’application ne doit pas s’exécuter.

     La <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> méthode appelle les méthodes suivantes :

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Détermine si l’application a un écran de démarrage défini et, le cas contraire, affiche l’écran de démarrage sur un thread séparé.

         La <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> méthode contient le code qui affiche l’écran de démarrage pendant au moins le nombre de millisecondes spécifié par la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> propriété. Pour utiliser cette fonctionnalité, vous devez ajouter l’écran de démarrage à votre application à l’aide du **Concepteur** de projets `My.Application.MinimumSplashScreenDisplayTime` (qui affecte à la propriété la valeur de `My.Application.MinimumSplashScreenDisplayTime` deux secondes) ou définir la propriété dans une <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> qui substitue la méthode ou. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Permet à un concepteur d’émettre du code qui initialise l’écran de démarrage.

         Par défaut, cette méthode ne fait rien. Si vous sélectionnez un écran de démarrage pour votre application dans le **Concepteur de projet**Visual Basic, le concepteur remplace la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> méthode par une méthode qui définit la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> propriété sur une nouvelle instance du formulaire d’écran de démarrage.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Fournit un point d’extensibilité pour déclencher `Startup` l’événement. La séquence de démarrage de l’application s’arrête `False`si cette fonction retourne.

     Par défaut, cette méthode déclenche l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> événement. Si le gestionnaire d’événements affecte <xref:System.ComponentModel.CancelEventArgs.Cancel> à la propriété de l’argument `True`d’événement la valeur `False` , la méthode retourne pour annuler le démarrage de l’application.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Fournit le point de départ lorsque l'application principale est prête à commencer son exécution, une fois l'initialisation faite.

     Par défaut, avant d’entrer dans la boucle de messages Windows Forms, cette méthode `OnCreateMainForm` appelle (pour créer le formulaire principal de l’application `HideSplashScreen` ) et les méthodes (pour fermer l’écran de démarrage) :

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Offre un moyen pour un concepteur d’émettre du code qui initialise le formulaire principal.

         Par défaut, cette méthode ne fait rien. Toutefois, lorsque vous sélectionnez un formulaire principal pour votre application dans le **Concepteur de projet**Visual Basic, le concepteur remplace la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> méthode par une méthode qui définit la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> propriété sur une nouvelle instance du formulaire principal.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Si un écran de démarrage est défini pour l’application et qu’il est ouvert, cette méthode ferme l’écran de démarrage.

         Par défaut, cette méthode ferme l’écran de démarrage.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Fournit un moyen de personnaliser le comportement d’une application à instance unique au démarrage d’une autre instance de l’application.

     Par défaut, cette méthode déclenche l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> événement.

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Fournit un point d’extensibilité pour déclencher `Shutdown` l’événement. Cette méthode ne s’exécute pas si une exception non gérée se produit dans l’application principale.

     Par défaut, cette méthode déclenche l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> événement.

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Exécuté si une exception non gérée se produit dans l’une des méthodes listées ci-dessus.

     Par défaut, cette méthode déclenche l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> événement tant qu’un débogueur n’est pas attaché et que l’application gère l' `UnhandledException` événement.

 Si l’application est une application à instance unique et que l’application est déjà en cours d’exécution, l’instance suivante de l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> application appelle la méthode sur l’instance d’origine de l’application, puis se termine.

 Le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> constructeur appelle la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> propriété pour déterminer le moteur de rendu de texte à utiliser pour les formulaires de l’application. Par défaut, la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> propriété retourne `False`, indiquant que le moteur de rendu de texte GDI doit être utilisé, qui est la valeur par défaut dans Visual Basic 2005 et versions ultérieures. Vous pouvez substituer la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> propriété pour retourner `True`, ce qui indique que le moteur de rendu de texte GDI+ doit être utilisé, qui est la valeur par défaut dans Visual Basic .NET 2002 et Visual Basic .NET 2003.

## <a name="configuring-the-application"></a>Configuration de l’application

 Dans le cadre du modèle d’application Visual Basic, la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> classe fournit des propriétés protégées qui configurent l’application. Ces propriétés doivent être définies dans le constructeur de la classe d’implémentation.

 Dans un projet Windows Forms par défaut, le **Concepteur de projets** crée du code pour définir les propriétés à l’aide des paramètres du concepteur. Les propriétés sont utilisées uniquement lorsque l’application démarre ; leur définition après le démarrage de l’application n’a aucun effet.

|Propriété|Permet|Paramètre dans le volet application du concepteur de projets|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Si l’application s’exécute en tant qu’application à instance unique ou à instances multiples.|Case à cocher **application à instance unique**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Si l’application utilise des styles visuels qui correspondent à Windows XP.|Case à cocher **activer les styles visuels XP**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Si l’application enregistre automatiquement les modifications apportées aux paramètres utilisateur lors de la fermeture de l’application.|Case à cocher **Enregistrer My. Settings lors de l’arrêt**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Ce qui entraîne l’arrêt de l’application, par exemple lors de la fermeture du formulaire de démarrage ou de la fermeture du dernier formulaire.|Liste des **modes d’arrêt**|

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Vue d’ensemble du modèle d’application Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Page Application, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
