# Star Bionic (Compose)

Jetpack Compose UI fork of the **Star Bionic** Winlator line. Runs Windows games and applications on Android by combining Wine, Box86/Box64, and the Adreno-tuned Turnip Vulkan driver. This fork's distinguishing work is the full migration of the legacy Java/XML UI to Jetpack Compose with Material 3.

- **Package:** `com.winlator.cmod`
- **Version:** `v1.2-REVAMPED` (build identifier `7.1.4x-cmod`, versionCode `20`)
- **Android SDK:** `compileSdk 34`, `targetSdk 28`, `minSdk 26` (Android 8.0+)
- **Upstream lineage:** Winlator → cmod → Bionic Nightly → Star → Star Bionic (Compose)

---

## What's in this fork

- **Full Jetpack Compose UI.** Every user-facing screen, dialog, drawer, and overlay has been ported off Java/XML to Compose + Material 3. This is the only Winlator fork to do this.
- **In-game Compose overlays.** Side drawer, settings dialogs, screen-effects panel, and task manager all run as Compose `Dialog` windows over the X server.
- **Dynamic theme system.** `AppThemeState` + `ThemePreset` allow live color/theme switching.
- **Controller support restored to Star 1.1 parity.** SDL2 SoName symlink wired into the Compose splash install path; all four controller event files pre-created at startup.
- **Box64 dropdown bug fix.** Edit-dialog now seeds the Box64 selector from the saved container value instead of resetting on dependency refresh.
- **Bionic content pattern.** Ships the larger `container_pattern_common.tzst` (bionic build, ~77 MB) for an expanded Start menu toolset.
- **Adreno-tuned drivers bundled.** Turnip 25.1.0, AdrenoTools v819, and Wrapper variants (gamenative, leegao, legacy, original).
- **Remote content registry.** Components (DXVK, VKD3D, wrappers, Box variants) are pulled from the **Bionic Nightly** registry maintained by Xnick417x.

---

## Building

This project is built via **GitHub Actions only**. Local builds are not supported.

- **Any branch:** push and trigger the `Any branch compilation` workflow.
- **Releases (main only):** trigger the `Manual Release Build` workflow.

Artifacts are published as workflow artifacts; tagged stable builds are also published as GitHub Releases.

---

## Branch model

- `main` — last shipped stable.
- `beta-N` — current integration branch where features land.
- `feature/*`, `fix/*`, `docs/*` — short-lived branches that merge into `beta-N`.

Features only reach `main` when the active `beta-N` is declared ready.

---

## Documentation in this repo

- `COMPOSE_MIGRATION_REPORT.md` — developer guide for the Java/XML → Compose migration (Parts A–G), including patterns, gotchas, and the engine boundary.
- `PROGRESS_LOG.md` — chronological record of every shipped change.
- `UI_MIGRATION_REPORT.md` — remaining UI cleanup and migration plan.

---

## Credits

This fork stands on a long chain of prior work. Credit, in lineage order:

| Contributor | Contribution |
|---|---|
| **brunodev85** | Original [Winlator](https://github.com/brunodev85/winlator) — Wine + Box64 + Turnip on Android. Foundation of every fork below. |
| **coffincolors** (cmod) | The `cmod` Winlator fork that introduced many of the customization features this codebase still relies on. |
| **Xnick417x** | Maintains the [Winlator-Bionic-Nightly-wcp](https://github.com/Xnick417x/Winlator-Bionic-Nightly-wcp) content registry. The registry JSON consumed by this fork: <https://raw.githubusercontent.com/Xnick417x/Winlator-Bionic-Nightly-wcp/refs/heads/main/content.json> |
| **jacojayy** | Maintainer of the [Star](https://github.com/jacojayy/star) line. SDK36 patches in the bundled Turnip driver for newer DXVK compatibility. |
| **vivsi** | Controller support contributions to the Star line that informed this fork's controller fixes. |
| **The412Banner** *(this repo's primary contributor)* | Full Jetpack Compose UI migration, in-game overlay rewrite, controller-support restore (SDL2 SoName fix + four event files), Box64 edit-dialog fix, theme system, and CI/release infrastructure. |
| **brunodev85** (re-credit) | The `input_controls` profiles served from <https://raw.githubusercontent.com/brunodev85/winlator/main/input_controls/> |

Credits surfaced in the **Star Bionic REVAMPED** release (`star.bionic-revamp`):

- **@The412Banner** — Converting the UI to Jetpack Compose and rewriting the controller implementation.
- **@jacojayy** — SDK36 patches in Turnip.

If you have contributed and are not listed, open an issue or PR — this list is intended to be complete.

---

## Disclaimer

Winlator and its forks are unofficial community projects. They are not affiliated with or endorsed by Microsoft, Wine, the Mesa project, Qualcomm, or any game publisher. Compatibility varies by device GPU, Android version, and individual game.

---

## License

Inherits the license of the upstream Winlator project (GPL-3.0). See `LICENSE` for the full text.
