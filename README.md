```
PRODUCT_PACKAGES += Via
```
---

### Exemplo 
```
# Clone Via browser to packages/apps/Via
echo -e "${CYAN}Cloning Via browser...${RESET}"
mkdir -p packages/apps/Via
git clone --depth 1 https://github.com/AviumUI/android_packages_apps_Via.git packages/apps/Via
rm -rf packages/apps/Via/.git
print_header "Via browser cloned to packages/apps/Via"

# Cleanup vendor
rm -rf vendor/lineage
print_header "Vendor cleanup completed"

# Clone modified vendor
clone_repo "https://github.com/sapphire-sm6225/android_vendor_lineage.git" "lineage-23.2" "vendor/lineage"

# Add Via browser to device.mk
DEVICE_MK="device/xiaomi/sapphire/device.mk"
if [ -f "$DEVICE_MK" ]; then
    echo "PRODUCT_PACKAGES += Via" >> "$DEVICE_MK"
    print_header "Via added to device.mk"
else
    echo -e "${YELLOW}device.mk not found, skipping Via addition${RESET}"
fi
```
