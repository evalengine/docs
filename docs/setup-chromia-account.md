---
sidebar_position: 4
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Setup Chromia Account

## Install Chromia CLI





You can install Chromia CLI using a package manager or by downloading it directly from [Chromia CLI Packages](https://gitlab.com/chromaway/core-tools/chromia-cli/-/packages).


<Tabs>
  <TabItem value="macos" label="macOS">

To install Chromia CLI (`chr`) on macOS, follow these steps:

1. If Homebrew is not installed, install it by running:

   ```sh
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. Add the Chromia repository to Homebrew by running the following command:

   ```sh
   brew tap chromia/core https://gitlab.com/chromaway/core-tools/homebrew-chromia.git
   ```

3. Install Chromia CLI with:

   ```sh
   brew install chromia/core/chr
   ```

4. To verify the installation, check the version by running:

   ```sh
   chr --version
   ```

  </TabItem>

  <TabItem value="linux" label="Linux/WSL">

To install Chromia CLI (`chr`) on Linux or WSL (Windows Subsystem for Linux), follow these steps:

1. Download and add Chromia's `apt-repo` public key to your system’s trusted keyrings:

   ```sh
   curl -fsSL https://apt.chromia.com/chromia.gpg | sudo tee /usr/share/keyrings/chromia.gpg
   ```

2. Add the Chromia repository to your list of package sources:

   ```sh
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/chromia.gpg] https://apt.chromia.com stable main" | sudo tee /etc/apt/sources.list.d/chromia.list
   ```

3. Run the following command to update your package sources:

   ```sh
   sudo apt-get update
   ```

   > **Info**: If you added `apt.chromia.com` before Chromia CLI version `0.16.0`, run the following command to allow the repository update:
   >
   > ```sh
   > sudo apt-get --allow-releaseinfo-change update
   > ```

4. Once the repository is updated, install Chromia CLI by running:

   ```sh
   sudo apt-get install chr
   ```

5. To verify that Chromia CLI is installed successfully, check the version:

   ```sh
   chr --version
   ```

  </TabItem>

  <TabItem value="windows" label="Windows">

To install Chromia CLI (`chr`) on Windows using [Scoop](https://scoop.sh/), follow these steps:

1. If Scoop is not installed, install it by running the following command in PowerShell (run as Administrator):

   ```powershell
   iwr -useb get.scoop.sh | iex
   ```

2. Add the Chromia repository (bucket) to Scoop by running:

   ```powershell
   scoop bucket add chromia https://gitlab.com/chromaway/core-tools/scoop-chromia/
   ```

3. Add the Java bucket to Scoop by running:

   ```powershell
   scoop bucket add java
   ```

   This will enable Scoop to download the OpenJDK 21, which Chromia CLI depends on when installing.

4. Install Chromia CLI by running:

   ```powershell
   scoop install chr
   ```

5. To verify that Chromia CLI is installed successfully, check the version:

   ```powershell
   chr --version
   ```

  </TabItem>
</Tabs>



## Create Private Keys

```
chr keygen -f eval_engine_key
```

You can find the generated private key in the `eval_engine_key` file. Save this private key in your environment variables.

The file will contain content similar to this:

```
#Keypair generated using secp256k1
#Sat Jan 25 08:25:39 MYT 2025
privkey=XXXXX
pubkey=XXXXX

```

> **Important:** Do not commit the `eval_engine_key` file to git version control




