---
title: Mettre en cache les données d’application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: b7d999f94e2f2ae410a16e537d51c0f890def4e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728061"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Procédure pas à pas : mise en cache de données d'application dans une application WPF
La mise en cache vous permet de stocker des données en mémoire pour y accéder rapidement. Quand vous accédez à nouveau aux données, les applications peuvent obtenir les données à partir du cache au lieu de devoir les récupérer à partir de la source d’origine. Cela peut améliorer les performances et la scalabilité. La mise en cache rend également les données disponibles quand la source de données est temporairement indisponible.

 Le .NET Framework fournit des classes qui vous permettent d’utiliser la mise en cache dans les applications .NET Framework. Ces classes se trouvent dans l’espace de noms <xref:System.Runtime.Caching>.

> [!NOTE]
> L’espace de noms <xref:System.Runtime.Caching> est une nouveauté du .NET Framework 4. Cet espace de noms rend la mise en cache disponible pour toutes les applications .NET Framework. Dans les versions précédentes de la .NET Framework, la mise en cache était uniquement disponible dans l’espace de noms <xref:System.Web> et nécessitait donc une dépendance sur les classes ASP.NET.

 Cette procédure pas à pas vous montre comment utiliser les fonctionnalités de mise en cache disponibles dans le .NET Framework dans le cadre d’une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Dans la procédure pas à pas, vous mettez en cache le contenu d’un fichier texte.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet d’application WPF.

- Ajout d’une référence au .NET Framework 4.

- Initialisation d’un cache.

- Ajout d’une entrée de cache qui contient le contenu d’un fichier texte.

- Fournir une stratégie d’éviction pour l’entrée du cache.

- Surveillance du chemin d’accès du fichier mis en cache et notification à l’instance du cache des modifications apportées à l’élément analysé.

## <a name="prerequisites"></a>Prerequisites
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Visual Studio 2010.

- Fichier texte qui contient une petite quantité de texte. (Le contenu du fichier texte s’affiche dans une boîte de message.) Le code illustré dans la procédure pas à pas suppose que vous travaillez avec le fichier suivant :

     `c:\cache\cacheText.txt`

     Toutefois, vous pouvez utiliser n’importe quel fichier texte et apporter des modifications mineures au code dans cette procédure pas à pas.

## <a name="creating-a-wpf-application-project"></a>Création d’un projet d’application WPF
 Vous allez commencer par créer un projet d’application WPF.

#### <a name="to-create-a-wpf-application"></a>Pour créer une application WPF

1. Démarrez Visual Studio.

2. Dans le menu **fichier** , cliquez sur **nouveau**, puis sur **nouveau projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Sous **modèles installés**, sélectionnez le langage de programmation que vous souhaitez utiliser (**Visual Basic** ou **C#visuel**).

4. Dans la boîte de dialogue **nouveau projet** , sélectionnez **application WPF**.

    > [!NOTE]
    > Si vous ne voyez pas le modèle d' **application WPF** , assurez-vous que vous ciblez une version du .NET Framework qui prend en charge WPF. Dans la boîte de dialogue **nouveau projet** , sélectionnez .NET Framework 4 dans la liste.

5. Dans la zone de texte **nom** , entrez un nom pour votre projet. Par exemple, vous pouvez entrer **WPFCaching**.

6. Cochez la case **Créer le répertoire pour la solution**.

7. Cliquez sur **OK**.

     Le Concepteur WPF s’ouvre en mode **création** et affiche le fichier MainWindow. Xaml. Visual Studio crée le dossier **My Project** , le fichier application. xaml et le fichier MainWindow. Xaml.

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Ciblage de la .NET Framework et ajout d’une référence aux assemblys de mise en cache
 Par défaut, les applications WPF ciblent le profil client .NET Framework 4. Pour utiliser l’espace de noms <xref:System.Runtime.Caching> dans une application WPF, l’application doit cibler le .NET Framework 4 (et non le .NET Framework 4 Client Profile) et doit inclure une référence à l’espace de noms.

 Par conséquent, l’étape suivante consiste à modifier le .NET Framework cible et à ajouter une référence à l’espace de noms <xref:System.Runtime.Caching>.

> [!NOTE]
> La procédure de modification de la .NET Framework cible est différente dans un projet Visual Basic et dans un C# projet visuel.

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Pour modifier le .NET Framework cible dans Visual Basic

1. Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**.

     La fenêtre Propriétés de l’application s’affiche.

2. Cliquez sur l’onglet **Compiler**.

3. En bas de la fenêtre, cliquez sur **Options avancées de compilation...** .

     La boîte de dialogue **Paramètres avancés du compilateur** s’affiche.

4. Dans la liste **Framework cible (toutes les configurations)** , sélectionnez .NET Framework 4. (Ne sélectionnez pas .NET Framework 4 Client Profile.)

5. Cliquez sur **OK**.

     La boîte de dialogue **Modification du Framework cible** s’affiche.

6. Dans la boîte de dialogue **modification du Framework cible** , cliquez sur **Oui**.

     Le projet est fermé, puis rouvert.

7. Ajoutez une référence à l’assembly de mise en cache en procédant comme suit :

    1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Ajouter une référence**.

    2. Sélectionnez l’onglet **.net** , sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Pour modifier le .NET Framework cible dans un projet C# visuel

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**.

     La fenêtre Propriétés de l’application s’affiche.

2. Cliquez sur l’onglet **Application** .

3. Dans la liste **Framework cible** , sélectionnez .NET Framework 4. (Ne sélectionnez pas **.NET Framework 4 Client Profile**.)

4. Ajoutez une référence à l’assembly de mise en cache en procédant comme suit :

    1. Cliquez avec le bouton droit sur le dossier **références** , puis cliquez sur **Ajouter une référence**.

    2. Sélectionnez l’onglet **.net** , sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.

## <a name="adding-a-button-to-the-wpf-window"></a>Ajout d’un bouton à la fenêtre WPF
 Ensuite, vous allez ajouter un contrôle Button et créer un gestionnaire d’événements pour l’événement `Click` du bouton. Plus tard, vous ajouterez le code à. ainsi, lorsque vous cliquerez sur le bouton, le contenu du fichier texte sera mis en cache et affiché.

#### <a name="to-add-a-button-control"></a>Pour ajouter un contrôle Button

1. Dans **Explorateur de solutions**, double-cliquez sur le fichier MainWindow. XAML pour l’ouvrir.

2. À partir de la **boîte à outils**, sous **contrôles WPF communs**, faites glisser un contrôle `Button` vers la fenêtre de `MainWindow`.

3. Dans la fenêtre **Propriétés** , affectez à la propriété `Content` du contrôle `Button` la valeur récupérer dans le **cache**.

## <a name="initializing-the-cache-and-caching-an-entry"></a>Initialisation du cache et mise en cache d’une entrée
 Ensuite, vous allez ajouter le code pour effectuer les tâches suivantes :

- Créez une instance de la classe cache, autrement dit, vous allez instancier un nouvel objet <xref:System.Runtime.Caching.MemoryCache>.

- Spécifiez que le cache utilise un objet <xref:System.Runtime.Caching.HostFileChangeMonitor> pour surveiller les modifications dans le fichier texte.

- Lit le fichier texte et met en cache son contenu en tant qu’entrée de cache.

- Affichez le contenu du fichier texte mis en cache.

#### <a name="to-create-the-cache-object"></a>Pour créer l’objet cache

1. Double-cliquez sur le bouton que vous venez d’ajouter afin de créer un gestionnaire d’événements dans le fichier MainWindow.xaml.cs ou MainWindow. Xaml. vb.

2. En haut du fichier (avant la déclaration de classe), ajoutez les instructions `Imports` (Visual Basic) ou `using` (C#) suivantes :

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. Dans le gestionnaire d’événements, ajoutez le code suivant pour instancier l’objet cache :

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     La classe <xref:System.Runtime.Caching.ObjectCache> est une classe intégrée qui fournit un cache d’objets en mémoire.

4. Ajoutez le code suivant pour lire le contenu d’une entrée de cache nommée `filecontents`:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. Ajoutez le code suivant pour vérifier si l’entrée de cache nommée `filecontents` existe :

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     Si l’entrée de cache spécifiée n’existe pas, vous devez lire le fichier texte et l’ajouter en tant qu’entrée de cache au cache.

6. Dans le bloc `if/then`, ajoutez le code suivant pour créer un nouvel objet <xref:System.Runtime.Caching.CacheItemPolicy> qui spécifie que l’entrée de cache expire au bout de 10 secondes.

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     Si aucune information d’éviction ou d’expiration n’est fournie, la valeur par défaut est <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, ce qui signifie que les entrées du cache n’expirent jamais en fonction d’une heure absolue. Au lieu de cela, les entrées de cache expirent uniquement en cas de sollicitation de la mémoire. En guise de meilleure pratique, vous devez toujours fournir explicitement une expiration absolue ou décalée.

7. Dans le bloc `if/then` et après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour créer une collection pour les chemins d’accès aux fichiers que vous souhaitez analyser, et pour ajouter le chemin d’accès du fichier texte à la collection :

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > Si le fichier texte que vous souhaitez utiliser n’est pas `c:\cache\cacheText.txt`, spécifiez le chemin d’accès du fichier texte que vous souhaitez utiliser.

8. Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour ajouter un nouvel objet <xref:System.Runtime.Caching.HostFileChangeMonitor> à la collection d’analyses de modification pour l’entrée de cache :

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     L’objet <xref:System.Runtime.Caching.HostFileChangeMonitor> surveille le chemin d’accès du fichier texte et avertit le cache si des modifications se produisent. Dans cet exemple, l’entrée de cache expire si le contenu du fichier est modifié.

9. Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour lire le contenu du fichier texte :

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     L’horodateur de la date et de l’heure est ajouté afin que vous puissiez voir à quel moment l’entrée du cache expire.

10. Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour insérer le contenu du fichier dans l’objet cache en tant qu’instance de <xref:System.Runtime.Caching.CacheItem> :

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     Vous spécifiez des informations sur la façon dont l’entrée du cache doit être supprimée en passant l’objet <xref:System.Runtime.Caching.CacheItemPolicy> que vous avez créé précédemment en tant que paramètre.

11. Après le bloc `if/then`, ajoutez le code suivant pour afficher le contenu du fichier mis en cache dans une boîte de message :

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. Dans le menu **générer** , cliquez sur **générer WPFCaching** pour générer votre projet.

## <a name="testing-caching-in-the-wpf-application"></a>Test de la mise en cache dans l’application WPF
 Vous pouvez à présent tester l’application.

#### <a name="to-test-caching-in-the-wpf-application"></a>Pour tester la mise en cache dans l’application WPF

1. Appuyez sur CTRL+F5 pour exécuter l'application.

     La fenêtre `MainWindow` s’affiche.

2. Cliquez sur **récupérer le cache**.

     Le contenu mis en cache à partir du fichier texte s’affiche dans une boîte de message. Notez l’horodateur du fichier.

3. Fermez la boîte de message, puis cliquez à nouveau sur **récupérer le cache** .

     L’horodateur est inchangé. Cela indique que le contenu mis en cache est affiché.

4. Attendez au moins 10 secondes, puis cliquez à nouveau sur **obtenir le cache** .

     Cette fois, un nouvel horodateur s’affiche. Cela indique que la stratégie laisse l’entrée de cache expirer et que le nouveau contenu mis en cache est affiché.

5. Dans un éditeur de texte, ouvrez le fichier texte que vous avez créé. N’apportez aucune modification pour le moment.

6. Fermez la boîte de message, puis cliquez à nouveau sur **récupérer le cache** .

     Remarquez l’horodatage.

7. Apportez une modification au fichier texte, puis enregistrez le fichier.

8. Fermez la boîte de message, puis cliquez à nouveau sur **récupérer le cache** .

     Cette boîte de message contient le contenu mis à jour à partir du fichier texte et un nouvel horodateur. Cela indique que l’analyse de la modification du fichier hôte a expulsé l’entrée du cache immédiatement lorsque vous avez modifié le fichier, même si le délai d’expiration absolu n’a pas expiré.

    > [!NOTE]
    > Vous pouvez augmenter le temps d’éviction à 20 secondes ou plus afin de laisser plus de temps à apporter une modification dans le fichier.

## <a name="code-example"></a>Exemple de code
 Une fois que vous avez terminé cette procédure pas à pas, le code pour le projet que vous avez créé ressemble à l’exemple suivant.

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [Mise en cache dans les applications .NET Framework](../../performance/caching-in-net-framework-applications.md)
