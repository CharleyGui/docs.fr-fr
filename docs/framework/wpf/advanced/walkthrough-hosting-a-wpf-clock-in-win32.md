---
title: 'Procédure pas à pas : hébergement d’une horloge WPF dans Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 27e1a2e88beeacf8c2cd98f61b11542ee2341e8f
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433974"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Procédure pas à pas : hébergement d’une horloge WPF dans Win32

Pour placer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] des applications, <xref:System.Windows.Interop.HwndSource>utilisez, qui fournit le HWND qui contient [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] votre contenu. Tout d’abord, <xref:System.Windows.Interop.HwndSource>vous créez le, en lui attribuant des paramètres similaires à CreateWindow. Vous indiquez ensuite le <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu que vous souhaitez à l’intérieur de celui-ci. Enfin, vous récupérez le HWND à partir <xref:System.Windows.Interop.HwndSource>du. Cette procédure pas à pas montre comment créer une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] interne mixte qui réimplémente la boîte de dialogue **des propriétés de date et d’heure** du système d’exploitation.

## <a name="prerequisites"></a>Prérequis

Consultez [interopérabilité WPF et Win32](wpf-and-win32-interoperation.md).

## <a name="how-to-use-this-tutorial"></a>Comment utiliser ce didacticiel

Ce didacticiel se concentre sur les étapes importantes de la production d’une application d’interopérabilité. Ce didacticiel est associé à un exemple, l’exemple d’interopérabilité de l' [horloge Win32](https://go.microsoft.com/fwlink/?LinkID=160051), mais cet échantillon reflète le produit final. Ce didacticiel décrit les étapes comme si vous démarriez avec un projet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] existant, peut-être un projet préexistant, et que vous ajoutiez un hébergé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à votre application. Vous pouvez comparer votre produit final avec l’exemple d’interopérabilité de l' [horloge Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Procédure pas à pas de Windows Presentation Foundation dans Win32 (HwndSource)

Le graphique suivant illustre le produit final prévu pour ce didacticiel :

![Capture d’écran qui affiche la boîte de dialogue Propriétés de date et heure.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Vous pouvez recréer cette boîte de dialogue en C++ créant un projet Win32 dans Visual Studio et en utilisant l’éditeur de boîtes de dialogue pour créer les éléments suivants:

![Boîte de dialogue Propriétés de date et heure recréées](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(Vous n’avez pas [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] besoin d’utiliser pour utiliser <xref:System.Windows.Interop.HwndSource>, et vous n’avez pas besoin C++ d’utiliser [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour écrire des programmes, mais il s’agit d’un moyen assez courant de le faire et qui se prête bien à une explication de didacticiel progressive).

Vous devez effectuer cinq sous-étapes particulières pour placer une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge dans la boîte de dialogue:

1. Autorisez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] votre projet à appeler du code managé ( **/CLR**) en modifiant les [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]paramètres du projet dans.

2. Créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> dans une dll distincte.

3. Placez-le <xref:System.Windows.Interop.HwndSource>à l’intérieur d’un. <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

4. Obtenir un HWND pour cela <xref:System.Windows.Controls.Page> à l' <xref:System.Windows.Interop.HwndSource.Handle%2A> aide de la propriété.

5. Utilisez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour décider où placer le HWND au sein de l' [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application de plus grande taille

## <a name="clr"></a>/clr

La première étape consiste à transformer ce [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projet non managé en un projet qui peut appeler du code managé. Vous utilisez l’option du compilateur/clr, qui est liée aux DLL nécessaires que vous souhaitez utiliser et ajustez la méthode main pour une utilisation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]avec.

Pour activer l’utilisation du code managé à l' C++ intérieur du projet: Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **Propriétés**. Sur la page de propriétés **général** (valeur par défaut), remplacez la prise en `/clr`charge du Common Language Runtime par.

Ensuite, ajoutez des références aux DLL nécessaires [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pour: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll et UIAutomationTypes. dll. Les instructions suivantes supposent que le système d’exploitation est installé sur le lecteur C:.

1. Cliquez avec le bouton droit sur le projet win32clock,, puis sélectionnez **références...** et à l’intérieur de cette boîte de dialogue:

2. Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .

3. Cliquez sur **Ajouter une nouvelle référence**, cliquez sur l’onglet Parcourir, entrez C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, puis cliquez sur OK.

4. Répétez la procédure pour PresentationFramework. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. Répétez la procédure pour WindowsBase. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Répétez la même opération pour UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Répétez la procédure pour UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. Cliquez sur **Ajouter une nouvelle référence**, sélectionnez System. dll, puis cliquez sur **OK**.

9. Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.

 Enfin, ajoutez `STAThreadAttribute` à la méthode `_tWinMain` pour l’utiliser avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Cet attribut indique au Common Language Runtime (CLR) que lorsqu’il initialise le modèle COM (Component Object Model), il doit utiliser un modèle STA (Single-Threaded Apartment), qui est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nécessaire pour [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)](et).

## <a name="create-a-windows-presentation-framework-page"></a>Créer une page Windows Presentation Framework

Ensuite, vous créez une DLL qui définit un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Page> Il est souvent plus facile de créer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le <xref:System.Windows.Controls.Page> comme une application autonome, et d’écrire et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de déboguer la partie de cette façon. Une fois terminé, ce projet peut être converti en DLL en cliquant avec le bouton droit sur le projet, en cliquant sur **Propriétés**, en accédant à l’application et en remplaçant le type de sortie par bibliothèque de classes Windows.

Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projet dll peut ensuite être combiné avec le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projet (une solution qui contient deux projets): cliquez avec le bouton droit sur la solution, puis sélectionnez **projet Add\Existing**.

Pour utiliser cette [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll à partir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] du projet, vous devez ajouter une référence:

1. Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .

2. Cliquez sur **Ajouter une nouvelle référence**.

3. Cliquez sur l’onglet **Projets**. Sélectionnez WPFClock, puis cliquez sur OK.

4. Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.

## <a name="hwndsource"></a>HwndSource

Ensuite, vous utilisez <xref:System.Windows.Interop.HwndSource> pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> donner un aspect à un HWND. Ajoutez ce bloc de code dans un fichier C++ :

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 Il s’agit d’un long bloc de code qui mérite une explication. La première partie est constituée de diverses clauses qui vous évitent d’avoir à qualifier complètement tous les appels :

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 Ensuite, vous définissez une fonction qui crée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu, en <xref:System.Windows.Interop.HwndSource> met une autour et retourne le HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Tout d’abord, <xref:System.Windows.Interop.HwndSource>vous créez un, dont les paramètres sont similaires à CreateWindow:

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

Ensuite, vous créez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la classe de contenu en appelant son constructeur:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Vous connectez ensuite la page à <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 Et dans la dernière ligne, retournez le HWND pour <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Positionnement du Hwnd

Maintenant que vous avez un HWND qui contient l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge, vous devez placer ce HWND dans la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] boîte de dialogue. Si vous saviez simplement où placer le HWND, vous devez simplement passer cette taille et cet emplacement à la `GetHwnd` fonction que vous avez définie précédemment. Toutefois, étant donné que vous avez utilisé un fichier de ressources pour définir la boîte de dialogue, vous ne savez pas exactement où les HWND sont positionnés. Vous pouvez utiliser l' [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] éditeur de boîtes de dialogue [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour placer un contrôle statique à l’emplacement où vous souhaitez placer l’horloge («insérer l’horloge ici») et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’utiliser pour positionner l’horloge.

Lorsque vous gérez WM_INITDIALOG, vous utilisez `GetDlgItem` pour récupérer le HWND pour l’espace réservé static:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Vous calculez ensuite la taille et la position de cet espace réservé statique. vous pouvez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donc placer l’horloge à cet endroit:

RECT rectangle;

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

Ensuite, masquez l’espace réservé STATIC :

```cpp
ShowWindow(placeholder, SW_HIDE);
```

Et créer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND Clock à cet emplacement:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Pour rendre le didacticiel intéressant et produire une horloge réelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , vous devez créer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle Clock à ce stade. Cette procédure se fait principalement en langage de balisage, avec quelques gestionnaires d’événements dans le code-behind. Étant donné que ce didacticiel concerne l’interopérabilité et non la conception des contrôles, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code complet de l’horloge est fourni ici en tant que bloc de code, sans instructions discrètes pour sa création ou ce que signifie chaque partie. N’hésitez pas à tester ce code pour changer l’apparence ou la fonctionnalité du contrôle.

Voici le code XAML :

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

Voici le code-behind correspondant :

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

Le résultat final ressemble à ceci :

![Boîte de dialogue Propriétés de date et heure du résultat final](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

Pour comparer votre résultat final au code qui a produit cette capture d’écran, consultez [exemple d’interopérabilité Win32 Clock](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndSource>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Interopérabilité Win32 Clock, exemple](https://go.microsoft.com/fwlink/?LinkID=160051)
