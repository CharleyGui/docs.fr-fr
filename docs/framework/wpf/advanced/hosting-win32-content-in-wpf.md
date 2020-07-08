---
title: Hébergement de contenu Win32
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: c0c62f1999feaf591c512314515f01e83fa12591
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052089"
---
# <a name="hosting-win32-content-in-wpf"></a>Hébergement de contenu Win32 dans WPF

## <a name="prerequisites"></a>Prérequis

Consultez [interopérabilité WPF et Win32](wpf-and-win32-interoperation.md).

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Procédure pas à pas de Win32 dans Windows Presentation Framework (HwndHost)

Pour réutiliser du contenu Win32 dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des applications, utilisez <xref:System.Windows.Interop.HwndHost> , qui est un contrôle qui donne à HWND un aspect similaire au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu. Comme <xref:System.Windows.Interop.HwndSource> , <xref:System.Windows.Interop.HwndHost> est simple à utiliser : dérivez de <xref:System.Windows.Interop.HwndHost> et implémentez les `BuildWindowCore` `DestroyWindowCore` méthodes et, puis instanciez votre <xref:System.Windows.Interop.HwndHost> classe dérivée et placez-la dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.

Si votre logique Win32 est déjà empaquetée en tant que contrôle, votre `BuildWindowCore` implémentation est légèrement plus simple qu’un appel à `CreateWindow` . Par exemple, pour créer un contrôle LISTBOX Win32 en C++ :

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

Mais supposons que le code Win32 n’est pas tout à fait autonome ? Dans ce cas, vous pouvez créer une boîte de dialogue Win32 et incorporer son contenu dans une application plus volumineuse [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . L’exemple illustre cela dans Visual Studio et C++, bien qu’il soit également possible de le faire dans un autre langage ou sur la ligne de commande.

Démarrez avec une boîte de dialogue simple, qui est compilée dans un projet DLL C++.

Ensuite, introduisez la boîte de dialogue dans l’application la plus volumineuse [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :

- Compilez la DLL comme géré ( `/clr` )

- Transformez la boîte de dialogue en contrôle

- Définir la classe dérivée de <xref:System.Windows.Interop.HwndHost> avec les `BuildWindowCore` `DestroyWindowCore` méthodes et

- Méthode override `TranslateAccelerator` pour gérer les touches de boîte de dialogue

- Méthode override `TabInto` pour prendre en charge la tabulation

- Substituer la `OnMnemonic` méthode pour prendre en charge les mnémoniques

- Instancier la <xref:System.Windows.Interop.HwndHost> sous-classe et la placer sous l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] élément de droite

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

Cette action ne l’empaquette pas entièrement dans un contrôle autonome ; vous devez toujours appeler `IsDialogMessage()` pour que Win32 puisse traiter certains messages, mais la modification de contrôle offre un moyen simple de placer ces contrôles à l’intérieur d’un autre HWND.

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

Créez ensuite une classe dérivée de <xref:System.Windows.Interop.HwndHost> et substituez `BuildWindowCore` les `DestroyWindowCore` méthodes et :

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

Ici, vous utilisez le `CreateDialog` pour créer la boîte de dialogue qui est vraiment un contrôle. Étant donné qu’il s’agit de l’une des premières méthodes appelées dans la DLL, vous devez également effectuer une initialisation Win32 standard en appelant une fonction que vous allez définir ultérieurement, appelée `InitializeGlobals()` :

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

Si vous avez exécuté cet exemple maintenant, vous obtiendriez un contrôle de boîte de dialogue qui s’affiche, mais il ignore tout le traitement du clavier qui fait apparaître une boîte de dialogue dans une boîte de dialogue fonctionnelle. Vous devez maintenant remplacer l' `TranslateAccelerator` implémentation (qui provient de `IKeyboardInputSink` , une interface qui <xref:System.Windows.Interop.HwndHost> implémente). Cette méthode est appelée lorsque l’application reçoit WM_KEYDOWN et WM_SYSKEYDOWN.

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

Il s’agit d’une grande quantité de code en une seule partie, afin de pouvoir utiliser des explications plus détaillées. Tout d’abord, le code utilisant les macros C++ et C++; vous devez savoir qu’il existe déjà une macro nommée `TranslateAccelerator` , qui est définie dans winuser. h :

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Veillez donc à définir une `TranslateAccelerator` méthode et non une `TranslateAcceleratorW` méthode.

De même, il existe à la fois le message winuser. h et le struct managé non managés `Microsoft::Win32::MSG` . Vous pouvez lever l’ambiguïté entre les deux à l’aide de l' `::` opérateur C++.

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}
```

Les deux messages ont les mêmes données, mais il est parfois plus facile de travailler avec la définition non gérée. par conséquent, dans cet exemple, vous pouvez définir la routine de conversion évidente :

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

Retour à `TranslateAccelerator` . Le principe de base consiste à appeler la fonction Win32 `IsDialogMessage` pour faire autant de travail que possible, mais `IsDialogMessage` n’a accès à rien en dehors de la boîte de dialogue. En tant qu’onglet utilisateur dans la boîte de dialogue, lorsque la tabulation s’exécute au-delà du dernier contrôle dans notre boîte de dialogue, vous devez définir le focus sur la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] partie en appelant `IKeyboardInputSite::OnNoMoreStops` .

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

Pour finir, appelez `IsDialogMessage`. Toutefois, l’une des responsabilités d’une `TranslateAccelerator` méthode est d’indiquer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] si vous avez géré ou non la séquence de touches. Si vous ne l’avez pas gérée, l’événement d’entrée peut effectuer un tunneling et se propager dans le reste de l’application. Ici, vous allez exposer une particularité du traitement du messange du clavier et la nature de l’architecture d’entrée dans Win32. Malheureusement, `IsDialogMessage` ne retourne pas de la même façon qu’il gère une séquence de touches particulière. Pire encore, il appellera `DispatchMessage()` sur les séquences de touches qu’il ne doit pas gérer.  Vous devez donc effectuer une ingénierie à rebours `IsDialogMessage` et l’appeler uniquement pour les clés que vous savez qu’il gérera :

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

Maintenant que vous avez implémenté `TranslateAccelerator` , un utilisateur peut faire un pas à pas détaillé dans la boîte de dialogue et l’onglet dans l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application supérieure. Toutefois, un utilisateur ne peut pas revenir à la boîte de dialogue. Pour résoudre ce qui se passe, vous devez remplacer `TabInto` :

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

Pourquoi ne pas appeler `IsDialogMessage` ici ?  Vous avez le même problème que précédemment : vous devez être en mesure d’indiquer au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code si votre code gérait ou non la séquence de touches, et `IsDialogMessage` ne peut pas le faire. Il y a également un deuxième problème, car `IsDialogMessage` refuse de traiter le mnémonique si le HWND ayant le focus n’est pas à l’intérieur de la boîte de dialogue.

### <a name="instantiate-the-hwndhost-derived-class"></a>Instancier la classe dérivée HwndHost

Enfin, maintenant que toutes les prises en charge des touches et des onglets sont en place, vous pouvez placer votre <xref:System.Windows.Interop.HwndHost> dans l’application plus grande [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Si l’application principale est écrite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , le moyen le plus simple de la placer dans le bon endroit est de conserver un <xref:System.Windows.Controls.Border> élément vide à l’endroit où vous souhaitez placer le <xref:System.Windows.Interop.HwndHost> . Ici, vous créez un <xref:System.Windows.Controls.Border> nommé `insertHwndHostHere` :

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

Tout cela reste à trouver un bon emplacement dans la séquence de code pour instancier <xref:System.Windows.Interop.HwndHost> et le connecter à <xref:System.Windows.Controls.Border> . Dans cet exemple, vous allez le placer à l’intérieur du constructeur pour la <xref:System.Windows.Window> classe dérivée :

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
