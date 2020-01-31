---
title: 'Procédure pas à pas : héberger une horloge WPF dans Win32'
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 1fdc0c9ccf1464d7519a4c5935520de1206ca9bb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794156"
---
# <a name="walkthrough-host-a-wpf-clock-in-win32"></a>Procédure pas à pas : héberger une horloge WPF dans Win32

Pour placer des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans des applications Win32, utilisez <xref:System.Windows.Interop.HwndSource>, qui fournit le HWND qui contient le contenu de votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tout d’abord, vous créez le <xref:System.Windows.Interop.HwndSource>, en lui attribuant des paramètres similaires à CreateWindow. Ensuite, vous indiquez à la <xref:System.Windows.Interop.HwndSource> à propos du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] souhaité. Enfin, vous récupérez le HWND à partir du <xref:System.Windows.Interop.HwndSource>. Cette procédure pas à pas montre comment créer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mixte dans une application Win32 qui réimplémente la boîte de dialogue **des propriétés de date et d’heure** du système d’exploitation.

## <a name="prerequisites"></a>Prerequisites

Consultez [interopérabilité WPF et Win32](wpf-and-win32-interoperation.md).

## <a name="how-to-use-this-tutorial"></a>Utilisation de ce didacticiel

Ce didacticiel se concentre sur les étapes importantes de la production d’une application d’interopérabilité. Ce didacticiel est associé à un exemple, l' [exemple d’interopérabilité de l’horloge Win32](https://go.microsoft.com/fwlink/?LinkID=160051), mais cet échantillon reflète le produit final. Ce didacticiel décrit les étapes comme si vous travailliez avec un projet Win32 existant, peut-être un projet préexistant, et que vous ajoutiez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé à votre application. Vous pouvez comparer votre produit final avec l' [exemple d’interopérabilité de l’horloge Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Procédure pas à pas de Windows Presentation Foundation dans Win32 (HwndSource)

Le graphique suivant illustre le produit final prévu pour ce didacticiel :

![Capture d’écran qui affiche la boîte de dialogue Propriétés de date et heure.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Vous pouvez recréer cette boîte de dialogue en C++ créant un projet Win32 dans Visual Studio et en utilisant l’éditeur de boîtes de dialogue pour créer les éléments suivants :

![Boîte de dialogue Propriétés de date et heure recréées](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(Vous n’avez pas besoin d’utiliser Visual Studio pour utiliser <xref:System.Windows.Interop.HwndSource>, et vous n’avez pas besoin C++ d’utiliser pour écrire des programmes Win32, mais il s’agit d’un moyen assez courant de le faire et qui se prête bien à une explication progressive du didacticiel).

Vous devez effectuer cinq sous-étapes particulières pour placer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge dans la boîte de dialogue :

1. Autorisez votre projet Win32 à appeler du code managé ( **/CLR**) en modifiant les paramètres du projet dans Visual Studio.

2. Créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dans une DLL distincte.

3. Placez ce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> à l’intérieur d’un <xref:System.Windows.Interop.HwndSource>.

4. Obtenir un HWND pour ce <xref:System.Windows.Controls.Page> à l’aide de la propriété <xref:System.Windows.Interop.HwndSource.Handle%2A>.

5. Utiliser Win32 pour décider où placer le HWND dans une application Win32 plus grande

## <a name="clr"></a>/clr

La première étape consiste à transformer ce projet Win32 non managé en un projet qui peut appeler du code managé. Vous utilisez l’option du compilateur/clr, qui est liée aux DLL nécessaires que vous souhaitez utiliser et ajustez la méthode main pour une utilisation avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Pour activer l’utilisation du code managé dans le C++ projet : cliquez avec le bouton droit sur le projet win32clock,, puis sélectionnez **Propriétés**. Sur la page de propriétés **général** (valeur par défaut), modifiez la prise en charge du Common Language Runtime pour `/clr`.

Ensuite, ajoutez des références aux DLL nécessaires pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll et UIAutomationTypes. dll. Les instructions suivantes supposent que le système d’exploitation est installé sur le lecteur C:.

1. Cliquez avec le bouton droit sur le projet win32clock,, puis sélectionnez **références...** et à l’intérieur de cette boîte de dialogue :

2. Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .

3. Cliquez sur **Ajouter une nouvelle référence**, cliquez sur l’onglet Parcourir, entrez C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, puis cliquez sur OK.

4. Répétez la même procédure pour PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. Répétez la même procédure pour WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Répétez la même procédure pour UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Répétez la même procédure pour UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. Cliquez sur **Ajouter une nouvelle référence**, sélectionnez System. dll, puis cliquez sur **OK**.

9. Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.

 Enfin, ajoutez le `STAThreadAttribute` à la méthode `_tWinMain` à utiliser avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Cet attribut indique au common language runtime (CLR) que lorsqu’il initialise le modèle COM (Component Object Model), il doit utiliser un modèle STA (Single-Threaded Apartment), qui est nécessaire pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (et Windows Forms).

## <a name="create-a-windows-presentation-framework-page"></a>Créer une page Windows Presentation Framework

Ensuite, vous créez une DLL qui définit un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>. Il est souvent plus facile de créer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> en tant qu’application autonome, et d’écrire et de déboguer la partie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de cette façon. Une fois terminé, ce projet peut être converti en DLL en cliquant avec le bouton droit sur le projet, en cliquant sur **Propriétés**, en accédant à l’application et en remplaçant le type de sortie par bibliothèque de classes Windows.

Le projet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll peut ensuite être combiné avec le projet Win32 (une solution qui contient deux projets) : cliquez avec le bouton droit sur la solution, puis sélectionnez **projet Add\Existing**.

Pour utiliser cette [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll à partir du projet Win32, vous devez ajouter une référence :

1. Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .

2. Cliquez sur **Ajouter une nouvelle référence**.

3. Cliquez sur l’onglet **projets** . Sélectionnez WPFClock, puis cliquez sur OK.

4. Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.

## <a name="hwndsource"></a>HwndSource

Ensuite, vous utilisez <xref:System.Windows.Interop.HwndSource> pour que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> ressemble à un HWND. Ajoutez ce bloc de code dans un fichier C++ :

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

 Ensuite, vous définissez une fonction qui crée le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], met un <xref:System.Windows.Interop.HwndSource> autour et retourne le HWND :

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Tout d’abord, vous créez un <xref:System.Windows.Interop.HwndSource>, dont les paramètres sont similaires à CreateWindow :

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

Ensuite, vous créez la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en appelant son constructeur :

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Vous connectez ensuite la page à la <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 Et dans la dernière ligne, retournez le HWND pour l' <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Positionnement du Hwnd

Maintenant que vous avez un HWND qui contient le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge, vous devez placer ce HWND dans la boîte de dialogue Win32. Si vous saviez simplement où placer le HWND, vous devez simplement passer cette taille et cet emplacement à la fonction `GetHwnd` que vous avez définie précédemment. Toutefois, étant donné que vous avez utilisé un fichier de ressources pour définir la boîte de dialogue, vous ne savez pas exactement où les HWND sont positionnés. Vous pouvez utiliser l’éditeur de boîtes de dialogue de Visual Studio pour placer un contrôle statique Win32 à l’endroit où vous souhaitez que l’horloge se trouve (« insérer l’horloge ici ») et l’utiliser pour positionner le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge.

Lorsque vous gérez WM_INITDIALOG, vous utilisez `GetDlgItem` pour récupérer le HWND pour l’espace réservé STATIC :

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Vous calculez ensuite la taille et la position de cet espace réservé statique, de sorte que vous pouvez placer la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge à cet endroit :

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

Et créer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND horloge à cet emplacement :

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Pour rendre le didacticiel intéressant et produire une horloge de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] réelle, vous devrez créer un contrôle d’horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à ce stade. Cette procédure se fait principalement en langage de balisage, avec quelques gestionnaires d’événements dans le code-behind. Dans la mesure où ce didacticiel concerne l’interopérabilité et non la conception des contrôles, le code complet de l’horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est fourni ici comme bloc de code, sans instructions discrètes pour sa création ou ce que signifie chaque partie. N’hésitez pas à tester ce code pour changer l’apparence ou la fonctionnalité du contrôle.

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
