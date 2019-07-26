---
title: Hébergement de contenu Win32 dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: ee260d58cdb4dc971fc32ca5c889b459b6a48489
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484737"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="8937a-102">Hébergement de contenu Win32 dans WPF</span><span class="sxs-lookup"><span data-stu-id="8937a-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8937a-103">Prérequis</span><span class="sxs-lookup"><span data-stu-id="8937a-103">Prerequisites</span></span>

<span data-ttu-id="8937a-104">Consultez [interopérabilité WPF et Win32](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="8937a-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="8937a-105">Procédure pas à pas de Win32 dans Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="8937a-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="8937a-106">Pour réutiliser [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] du contenu à l' <xref:System.Windows.Interop.HwndHost>intérieur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des applications, utilisez, qui est un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui donne à HWND un aspect similaire au contenu.</span><span class="sxs-lookup"><span data-stu-id="8937a-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="8937a-107">Comme <xref:System.Windows.Interop.HwndSource>, `BuildWindowCore` <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `DestroyWindowCore` est simple à utiliser: dérivez de et implémentez les méthodes et, puis instanciez votre classe dérivée et placez-la à l’intérieur de votre <xref:System.Windows.Interop.HwndHost> oeuvre.</span><span class="sxs-lookup"><span data-stu-id="8937a-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="8937a-108">Si votre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logique est déjà empaquetée en tant que contrôle `BuildWindowCore` , votre implémentation est légèrement plus simple qu' `CreateWindow`un appel à.</span><span class="sxs-lookup"><span data-stu-id="8937a-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="8937a-109">Par exemple, pour créer un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôle ListBox dans C++:</span><span class="sxs-lookup"><span data-stu-id="8937a-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in C++:</span></span>

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

<span data-ttu-id="8937a-110">Mais supposons [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] que le code n’est pas tout à fait autonome?</span><span class="sxs-lookup"><span data-stu-id="8937a-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="8937a-111">Dans ce cas, vous pouvez créer [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] une boîte de dialogue et incorporer son contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une application plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="8937a-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="8937a-112">L’exemple illustre cela dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] et C++, bien qu’il soit également possible de le faire dans un autre langage ou sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8937a-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="8937a-113">Démarrez avec une boîte de dialogue simple, qui est compilée dans un C++ [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="8937a-113">Start with a simple dialog, which is compiled into a C++ [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>

<span data-ttu-id="8937a-114">Ensuite, introduisez la boîte de dialogue [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l’application la plus volumineuse:</span><span class="sxs-lookup"><span data-stu-id="8937a-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="8937a-115">Compiler comme managé (`/clr`) [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8937a-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>

- <span data-ttu-id="8937a-116">Transformez la boîte de dialogue en contrôle</span><span class="sxs-lookup"><span data-stu-id="8937a-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="8937a-117">Définir la classe dérivée <xref:System.Windows.Interop.HwndHost> de `BuildWindowCore` avec `DestroyWindowCore` les méthodes et</span><span class="sxs-lookup"><span data-stu-id="8937a-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="8937a-118">Méthode override `TranslateAccelerator` pour gérer les touches de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="8937a-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="8937a-119">Méthode override `TabInto` pour prendre en charge la tabulation</span><span class="sxs-lookup"><span data-stu-id="8937a-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="8937a-120">Substituer `OnMnemonic` la méthode pour prendre en charge les mnémoniques</span><span class="sxs-lookup"><span data-stu-id="8937a-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="8937a-121">Instancier <xref:System.Windows.Interop.HwndHost> la sous-classe et la placer sous [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’élément de droite</span><span class="sxs-lookup"><span data-stu-id="8937a-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="8937a-122">Transformez la boîte de dialogue en contrôle</span><span class="sxs-lookup"><span data-stu-id="8937a-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="8937a-123">Vous pouvez transformer une boîte de dialogue en un HWND enfant à l’aide des styles WS_CHILD et DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="8937a-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="8937a-124">Accédez au fichier de ressources (. RC) dans lequel la boîte de dialogue est définie et recherchez le début de la définition de la boîte de dialogue:</span><span class="sxs-lookup"><span data-stu-id="8937a-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="8937a-125">Remplacez la deuxième ligne par:</span><span class="sxs-lookup"><span data-stu-id="8937a-125">Change the second line to:</span></span>

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="8937a-126">Cette action ne l’empaquette pas entièrement dans un contrôle autonome; vous devez toujours appeler `IsDialogMessage()` pour que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] puisse traiter certains messages, mais la modification de contrôle offre un moyen simple de placer ces contrôles à l’intérieur d’un autre HWND.</span><span class="sxs-lookup"><span data-stu-id="8937a-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="8937a-127">Sous-classe HwndHost</span><span class="sxs-lookup"><span data-stu-id="8937a-127">Subclass HwndHost</span></span>

<span data-ttu-id="8937a-128">Importez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="8937a-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="8937a-129">Créez ensuite une classe dérivée <xref:System.Windows.Interop.HwndHost> de et substituez `BuildWindowCore` les `DestroyWindowCore` méthodes et:</span><span class="sxs-lookup"><span data-stu-id="8937a-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="8937a-130">Ici, vous utilisez `CreateDialog` le pour créer la boîte de dialogue qui est vraiment un contrôle.</span><span class="sxs-lookup"><span data-stu-id="8937a-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="8937a-131">Étant donné qu’il s’agit de l’une des premières [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]méthodes appelées dans le, vous [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] devez également effectuer une initialisation standard en appelant une fonction que vous `InitializeGlobals()`allez définir ultérieurement, appelée:</span><span class="sxs-lookup"><span data-stu-id="8937a-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="8937a-132">Substituez la méthode TranslateAccelerator pour gérer les touches de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="8937a-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="8937a-133">Si vous avez exécuté cet exemple maintenant, vous obtiendriez un contrôle de boîte de dialogue qui s’affiche, mais il ignore tout le traitement du clavier qui fait apparaître une boîte de dialogue dans une boîte de dialogue fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="8937a-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="8937a-134">Vous devez maintenant remplacer l' `TranslateAccelerator` implémentation (qui provient de `IKeyboardInputSink`, une interface qui <xref:System.Windows.Interop.HwndHost> implémente).</span><span class="sxs-lookup"><span data-stu-id="8937a-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="8937a-135">Cette méthode est appelée lorsque l’application reçoit WM_KEYDOWN et WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="8937a-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="8937a-136">Il s’agit d’une grande quantité de code en une seule partie, afin de pouvoir utiliser des explications plus détaillées.</span><span class="sxs-lookup"><span data-stu-id="8937a-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="8937a-137">Tout d’abord, le C++ code C++ utilisant les macros et. vous devez savoir qu’il existe déjà une macro nommée `TranslateAccelerator`, qui est définie dans winuser. h:</span><span class="sxs-lookup"><span data-stu-id="8937a-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="8937a-138">Veillez donc à définir une `TranslateAccelerator` méthode et non une `TranslateAcceleratorW` méthode.</span><span class="sxs-lookup"><span data-stu-id="8937a-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="8937a-139">De même, il existe à la fois le message winuser. h et le struct managé `Microsoft::Win32::MSG` non managés.</span><span class="sxs-lookup"><span data-stu-id="8937a-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="8937a-140">Vous pouvez lever l’ambiguïté entre les deux à l' C++ `::` aide de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="8937a-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

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

<span data-ttu-id="8937a-141">Retour à `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="8937a-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="8937a-142">Le principe de base consiste à appeler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] la `IsDialogMessage` fonction pour faire autant de travail que possible, `IsDialogMessage` mais n’a accès à rien en dehors de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8937a-142">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="8937a-143">En tant qu’onglet utilisateur dans la boîte de dialogue, lorsque la tabulation s’exécute au-delà du dernier contrôle dans notre boîte de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dialogue, vous `IKeyboardInputSite::OnNoMoreStops`devez définir le focus sur la partie en appelant.</span><span class="sxs-lookup"><span data-stu-id="8937a-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="8937a-144">Pour finir, appelez `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="8937a-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="8937a-145">Toutefois, l’une des responsabilités d' `TranslateAccelerator` une méthode est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’indiquer si vous avez géré ou non la séquence de touches.</span><span class="sxs-lookup"><span data-stu-id="8937a-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="8937a-146">Si vous ne l’avez pas gérée, l’événement d’entrée peut effectuer un tunneling et se propager dans le reste de l’application.</span><span class="sxs-lookup"><span data-stu-id="8937a-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="8937a-147">Ici, vous allez exposer une particularité du traitement du messange du clavier et la nature de l' [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]architecture d’entrée dans.</span><span class="sxs-lookup"><span data-stu-id="8937a-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="8937a-148">Malheureusement, `IsDialogMessage` ne retourne pas de la même façon qu’il gère une séquence de touches particulière.</span><span class="sxs-lookup"><span data-stu-id="8937a-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="8937a-149">Pire encore, il appellera `DispatchMessage()` sur les séquences de touches qu’il ne doit pas gérer.</span><span class="sxs-lookup"><span data-stu-id="8937a-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="8937a-150">Vous devez donc effectuer une ingénierie `IsDialogMessage`à rebours et l’appeler uniquement pour les clés que vous savez qu’il gérera:</span><span class="sxs-lookup"><span data-stu-id="8937a-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="8937a-151">Remplacer la méthode TabInto pour prendre en charge la tabulation</span><span class="sxs-lookup"><span data-stu-id="8937a-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="8937a-152">Maintenant que vous avez implémenté `TranslateAccelerator`, un utilisateur peut faire un pas à pas détaillé dans la boîte de dialogue et l’onglet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l’application supérieure.</span><span class="sxs-lookup"><span data-stu-id="8937a-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="8937a-153">Toutefois, un utilisateur ne peut pas revenir à la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8937a-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="8937a-154">Pour résoudre ce qui se passe, `TabInto`vous devez remplacer:</span><span class="sxs-lookup"><span data-stu-id="8937a-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="8937a-155">Le `TraversalRequest` paramètre indique si l’action de tabulation est un onglet de tabulation ou de décalage.</span><span class="sxs-lookup"><span data-stu-id="8937a-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="8937a-156">Remplacer la méthode OnMnemonic pour prendre en charge les mnémoniques</span><span class="sxs-lookup"><span data-stu-id="8937a-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="8937a-157">La gestion du clavier est presque terminée, mais il manque une chose: les mnémoniques ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="8937a-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="8937a-158">Si un utilisateur appuie sur ALT-F, le focus Doe n’accède pas à la zone d’édition «prénom:».</span><span class="sxs-lookup"><span data-stu-id="8937a-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="8937a-159">Par conséquent, vous devez substituer la `OnMnemonic` méthode:</span><span class="sxs-lookup"><span data-stu-id="8937a-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="8937a-160">Pourquoi ne pas `IsDialogMessage` appeler ici?</span><span class="sxs-lookup"><span data-stu-id="8937a-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="8937a-161">Vous avez le même problème que précédemment: vous devez être en mesure d’indiquer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au code si votre code gérait ou non la séquence de touches, et `IsDialogMessage` ne peut pas le faire.</span><span class="sxs-lookup"><span data-stu-id="8937a-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="8937a-162">Il y a également un deuxième problème, `IsDialogMessage` car refuse de traiter le mnémonique si le HWND ayant le focus n’est pas à l’intérieur de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8937a-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="8937a-163">Instancier la classe dérivée HwndHost</span><span class="sxs-lookup"><span data-stu-id="8937a-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="8937a-164">Enfin, maintenant que toutes les prises en charge des touches et des onglets sont en place <xref:System.Windows.Interop.HwndHost> , vous pouvez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] placer votre dans l’application plus grande.</span><span class="sxs-lookup"><span data-stu-id="8937a-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="8937a-165">Si l’application principale est écrite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], le moyen le plus simple de la placer dans le bon endroit est de conserver un élément vide <xref:System.Windows.Controls.Border> à l’endroit où vous <xref:System.Windows.Interop.HwndHost>souhaitez placer le.</span><span class="sxs-lookup"><span data-stu-id="8937a-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="8937a-166">Ici, vous créez <xref:System.Windows.Controls.Border> un `insertHwndHostHere`nommé:</span><span class="sxs-lookup"><span data-stu-id="8937a-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="8937a-167">Tout cela reste à trouver un bon emplacement dans la séquence de code pour instancier <xref:System.Windows.Interop.HwndHost> et le connecter <xref:System.Windows.Controls.Border>à.</span><span class="sxs-lookup"><span data-stu-id="8937a-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="8937a-168">Dans cet exemple, vous allez le placer à l’intérieur du constructeur <xref:System.Windows.Window> pour la classe dérivée:</span><span class="sxs-lookup"><span data-stu-id="8937a-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="8937a-169">Ce qui vous donne:</span><span class="sxs-lookup"><span data-stu-id="8937a-169">Which gives you:</span></span>

![Capture d’écran de l’application WPF en cours d’exécution.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="8937a-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8937a-171">See also</span></span>

- [<span data-ttu-id="8937a-172">Interopérabilité WPF et Win32</span><span class="sxs-lookup"><span data-stu-id="8937a-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
