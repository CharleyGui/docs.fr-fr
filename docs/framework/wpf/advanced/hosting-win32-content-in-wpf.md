---
title: Hébergement de contenu Win32 dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: b598b55c72096daac2487e4c52584abf9735f257
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991469"
---
# <a name="hosting-win32-content-in-wpf"></a>Hébergement de contenu Win32 dans WPF

## <a name="prerequisites"></a>Prérequis

Consultez [interopérabilité WPF et Win32](wpf-and-win32-interoperation.md).

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Procédure pas à pas de Win32 dans Windows Presentation Framework (HwndHost)

Pour réutiliser [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] du contenu à l' <xref:System.Windows.Interop.HwndHost>intérieur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des applications, utilisez, qui est un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui donne à HWND un aspect similaire au contenu. Comme <xref:System.Windows.Interop.HwndSource>, `BuildWindowCore` <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `DestroyWindowCore` est simple à utiliser : dérivez de et implémentez les méthodes et, puis instanciez votre classe dérivée et placez-la à l’intérieur de votre <xref:System.Windows.Interop.HwndHost> oeuvre.

Si votre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logique est déjà empaquetée en tant que contrôle `BuildWindowCore` , votre implémentation est légèrement plus simple qu' `CreateWindow`un appel à. Par exemple, pour créer un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôle ListBox dans C++:

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

Mais supposons [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] que le code n’est pas tout à fait autonome ? Dans ce cas, vous pouvez créer [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] une boîte de dialogue et incorporer son contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une application plus volumineuse. L’exemple illustre cela dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] et C++, bien qu’il soit également possible de le faire dans un autre langage ou sur la ligne de commande.

Démarrez avec une boîte de dialogue simple, qui est compilée dans un C++ projet dll.

Ensuite, introduisez la boîte de dialogue [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l’application la plus volumineuse :

- Compilez la DLL comme`/clr`géré ()

- Transformez la boîte de dialogue en contrôle

- Définir la classe dérivée <xref:System.Windows.Interop.HwndHost> de `BuildWindowCore` avec `DestroyWindowCore` les méthodes et

- Méthode override `TranslateAccelerator` pour gérer les touches de boîte de dialogue

- Méthode override `TabInto` pour prendre en charge la tabulation

- Substituer `OnMnemonic` la méthode pour prendre en charge les mnémoniques

- Instancier <xref:System.Windows.Interop.HwndHost> la sous-classe et la placer sous [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’élément de droite

### <a name="turn-the-dialog-into-a-control"></a>Transformez la boîte de dialogue en contrôle

Vous pouvez transformer une boîte de dialogue en un HWND enfant à l’aide des styles WS_CHILD et DS_CONTROL. Accédez au fichier de ressources (. RC) dans lequel la boîte de dialogue est définie et recherchez le début de la définition de la boîte de dialogue :

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

Remplacez la deuxième ligne par :

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Cette action ne l’empaquette pas entièrement dans un contrôle autonome ; vous devez toujours appeler `IsDialogMessage()` pour que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] puisse traiter certains messages, mais la modification de contrôle offre un moyen simple de placer ces contrôles à l’intérieur d’un autre HWND.

## <a name="subclass-hwndhost"></a>Sous-classe HwndHost

Importez les espaces de noms suivants :

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

Créez ensuite une classe dérivée <xref:System.Windows.Interop.HwndHost> de et substituez `BuildWindowCore` les `DestroyWindowCore` méthodes et :

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

Ici, vous utilisez `CreateDialog` le pour créer la boîte de dialogue qui est vraiment un contrôle. Étant donné qu’il s’agit de l’une des premières méthodes appelées dans la dll, vous [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] devez également effectuer une initialisation standard en appelant une fonction que vous `InitializeGlobals()`allez définir ultérieurement, appelée :

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Substituez la méthode TranslateAccelerator pour gérer les touches de boîte de dialogue

Si vous avez exécuté cet exemple maintenant, vous obtiendriez un contrôle de boîte de dialogue qui s’affiche, mais il ignore tout le traitement du clavier qui fait apparaître une boîte de dialogue dans une boîte de dialogue fonctionnelle. Vous devez maintenant remplacer l' `TranslateAccelerator` implémentation (qui provient de `IKeyboardInputSink`, une interface qui <xref:System.Windows.Interop.HwndHost> implémente). Cette méthode est appelée lorsque l’application reçoit WM_KEYDOWN et WM_SYSKEYDOWN.

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

Il s’agit d’une grande quantité de code en une seule partie, afin de pouvoir utiliser des explications plus détaillées. Tout d’abord, le C++ code C++ utilisant les macros et. vous devez savoir qu’il existe déjà une macro nommée `TranslateAccelerator`, qui est définie dans winuser. h :

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Veillez donc à définir une `TranslateAccelerator` méthode et non une `TranslateAcceleratorW` méthode.

De même, il existe à la fois le message winuser. h et le struct managé `Microsoft::Win32::MSG` non managés. Vous pouvez lever l’ambiguïté entre les deux à l' C++ `::` aide de l’opérateur.

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

Retour à `TranslateAccelerator`. Le principe de base consiste à appeler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] la `IsDialogMessage` fonction pour faire autant de travail que possible, `IsDialogMessage` mais n’a accès à rien en dehors de la boîte de dialogue. En tant qu’onglet utilisateur dans la boîte de dialogue, lorsque la tabulation s’exécute au-delà du dernier contrôle dans notre boîte de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dialogue, vous `IKeyboardInputSite::OnNoMoreStops`devez définir le focus sur la partie en appelant.

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

Pour finir, appelez `IsDialogMessage`. Toutefois, l’une des responsabilités d' `TranslateAccelerator` une méthode est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’indiquer si vous avez géré ou non la séquence de touches. Si vous ne l’avez pas gérée, l’événement d’entrée peut effectuer un tunneling et se propager dans le reste de l’application. Ici, vous allez exposer une particularité du traitement du messange du clavier et la nature de l' [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]architecture d’entrée dans. Malheureusement, `IsDialogMessage` ne retourne pas de la même façon qu’il gère une séquence de touches particulière. Pire encore, il appellera `DispatchMessage()` sur les séquences de touches qu’il ne doit pas gérer.  Vous devez donc effectuer une ingénierie `IsDialogMessage`à rebours et l’appeler uniquement pour les clés que vous savez qu’il gérera :

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a>Remplacer la méthode TabInto pour prendre en charge la tabulation

Maintenant que vous avez implémenté `TranslateAccelerator`, un utilisateur peut faire un pas à pas détaillé dans la boîte de dialogue et l’onglet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l’application supérieure. Toutefois, un utilisateur ne peut pas revenir à la boîte de dialogue. Pour résoudre ce qui se passe, `TabInto`vous devez remplacer :

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

Le `TraversalRequest` paramètre indique si l’action de tabulation est un onglet de tabulation ou de décalage.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Remplacer la méthode OnMnemonic pour prendre en charge les mnémoniques

La gestion du clavier est presque terminée, mais il manque une chose : les mnémoniques ne fonctionnent pas. Si un utilisateur appuie sur ALT-F, le focus Doe n’accède pas à la zone d’édition « prénom : ». Par conséquent, vous devez substituer la `OnMnemonic` méthode :

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

Pourquoi ne pas `IsDialogMessage` appeler ici ?  Vous avez le même problème que précédemment : vous devez être en mesure d’indiquer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au code si votre code gérait ou non la séquence de touches, et `IsDialogMessage` ne peut pas le faire. Il y a également un deuxième problème, `IsDialogMessage` car refuse de traiter le mnémonique si le HWND ayant le focus n’est pas à l’intérieur de la boîte de dialogue.

### <a name="instantiate-the-hwndhost-derived-class"></a>Instancier la classe dérivée HwndHost

Enfin, maintenant que toutes les prises en charge des touches et des onglets sont en place <xref:System.Windows.Interop.HwndHost> , vous pouvez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] placer votre dans l’application plus grande. Si l’application principale est écrite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], le moyen le plus simple de la placer dans le bon endroit est de conserver un élément vide <xref:System.Windows.Controls.Border> à l’endroit où vous <xref:System.Windows.Interop.HwndHost>souhaitez placer le. Ici, vous créez <xref:System.Windows.Controls.Border> un `insertHwndHostHere`nommé :

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

Tout cela reste à trouver un bon emplacement dans la séquence de code pour instancier <xref:System.Windows.Interop.HwndHost> et le connecter <xref:System.Windows.Controls.Border>à. Dans cet exemple, vous allez le placer à l’intérieur du constructeur <xref:System.Windows.Window> pour la classe dérivée :

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

Ce qui vous donne :

![Capture d’écran de l’application WPF en cours d’exécution.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>Voir aussi

- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
