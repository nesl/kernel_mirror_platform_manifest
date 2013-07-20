___Expected filesystem structure___

```
.
├── kernel -> /aosp/mirror/kernel
└── platform
    ├── manifest.git
    └── prebuilts
	└── gcc
	    └── linux-x86
		└── arm
		    └── arm-eabi-4.6.git -> /aosp/mirror/platform/prebuilts/gcc/linux-x86/arm/arm-eabi-4.6.git
```

The above is the output of `tree /aosp/kernel_mirror`

First checkout the local android mirror into `/aosp/mirrora
`
Then set up symbolic links: (in the abovel `->` denotes symbolic link to directories or `.git` repos)

Then do a bare clone.
`git clone --bare https://github.com/nesl/kernel_mirror_platform_manifest.git /aosp/kernel_mirror/platform/manifest.git`


After performing the above steps, you should be able to treat `/aosp/kernel_mirror` as special local mirror where
you can do the following: `repo init -u /aosp/kernel_mirror/platform/manifest.git`, then `repo sync` to checkout
the project.

*The `kernel` jenkins jobs uses this kernel mirror to facilitate building kernel projects.*

```
mkdir /aosp/kernel_mirror
mkdir -p /aosp/kernel_mirror/platform
git clone --bare https://github.com/nesl/kernel_mirror_platform_manifest /aosp/kernel_mirror/platform/manifest.git
ln -s /aosp/mirror/kernel /aosp/mirror/
mkdir -p /aosp/kernel_mirror/prebuilts/gcc/linux-x86/arm/
ln -s /aosp/mirror/platform/prebuilts/gcc/linux-x86/arm/arm-eabi-4.6.git /aosp/kernel_mirror/platform/prebuilts/gcc/linux-x86/arm/ 
```

