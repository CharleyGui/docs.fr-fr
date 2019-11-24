---
title: Install .NET Core on CentOS 7 - package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 62b07342197addaa5c7d962c08c4ff1d7121eff8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451079"
---
# <a name="centos-7-package-manager---install-net-core"></a>CentOS 7 Package Manager - Install .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

This article describes how to use a package manager to install .NET Core on CentOS 7. If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.

## <a name="register-microsoft-key-and-feed"></a>Register Microsoft key and feed

Before installing .NET, you'll need to:

- Register the Microsoft key
- register the product repository
- Install required dependencies

This only needs to be done once per machine.

Open a terminal and run the following command.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Install the .NET Core SDK

Update the products available for installation, then install the .NET Core SDK. In your terminal, run the following command.

```bash
sudo yum install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a>Install the ASP.NET Core runtime

Update the products available for installation, then install the ASP.NET runtime. In your terminal, run the following command.

```bash
sudo yum install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a>Install the .NET Core runtime

Update the products available for installation, then install the .NET Core runtime. In your terminal, run the following command.

```bash
sudo yum install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a>How to install other versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
