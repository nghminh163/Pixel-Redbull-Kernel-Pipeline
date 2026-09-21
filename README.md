# Pixel Redbull Kernel Pipeline

Pipeline build kernel cho Google Pixel 5 (**redfin**) / Pixel 4a 5G (**bramble**) — dòng
kernel `android-msm-redbull-4.19` — bằng GitHub Actions.

## Nhánh

| Nhánh | Nội dung |
|-------|----------|
| **`main`** | **Phase 1** — chỉ build kernel *không patch*, ra `boot.img`/`vendor_boot.img`/`dtbo.img` để chứng minh kernel custom được. KSU/SUSFS/modules sẽ mod dần. |
| **`main-legacy`** | Pipeline đầy đủ trước đây (KernelSU / KernelSU-Next / SUSFS + modules + prebuilt). Giữ để tham chiếu. |

> Ý tưởng: dựng nền build sạch trước (chứng minh compile + ra ảnh flash được), rồi thêm
> KernelSU → SUSFS → modules theo từng bước, mỗi bước build + kiểm chứng.

## Cách chạy (Phase 1)

1. Tab **Actions** → **Kernel build for redbull device** → **Run workflow**.
2. Chọn:
   - `device`: `redfin` (Pixel 5) hoặc `bramble` (Pixel 4a 5G)
   - `android_version`: branch manifest — **phải có ramdisk tương ứng** trong `ramdisk/<device>/<branch>/`.
3. Tải artifact `fastboot-<device>-<branch>` → chứa `fastboot.zip` (boot/vendor_boot/dtbo).

Ramdisk có sẵn hiện tại:
```
ramdisk/redfin/android-msm-redbull-4.19-android12/
ramdisk/redfin/android-msm-redbull-4.19-android14/
ramdisk/bramble/android-msm-redbull-4.19-android13-qpr3/
```

## Flow build (theo bản cũ)

`repo init/sync` nguồn kernel → chèn `ramdisk`/`vendor_ramdisk` gốc vào
`prebuilts/boot-artifacts/ramdisks/` → bỏ `check_defconfig` → `BUILD_AOSP_KERNEL=1 ./build_redbull-gki.sh`
→ đóng gói `boot.img`+`vendor_boot.img`+`dtbo.img` thành `fastboot.zip`.

## Flash

```bash
unzip fastboot.zip
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot flash dtbo dtbo.img
# hoặc test tạm: fastboot boot boot.img
```

## Lộ trình

- [x] Phase 1: build kernel không patch → ảnh flash.
- [ ] Phase 2: KernelSU-Next.
- [ ] Phase 3: SUSFS.
- [ ] Phase 4: modules (ReZygisk, LSPosed, PlayIntegrityFix, TrickyStore…).
