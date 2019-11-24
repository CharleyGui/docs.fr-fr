---
title: Install .NET Core on Linux RHEL 7 package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 4893271ebd32036d8ec09e6b718c12b11acb8d59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450981"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 Package Manager - Install .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

This article describes how to use a package manager to install .NET Core on RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Register your Red Hat subscription

To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager. If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Install the .NET Core SDK

After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK. In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install .

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Install the ASP.NET Core Runtime

After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime. In your terminal, run the following commands.

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a>Install the .NET Core Runtime

After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime. In your terminal, run the following commands.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```
