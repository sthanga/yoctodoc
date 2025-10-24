# Uboot details
# https://www.nxp.com/docs/en/user-guide/GOOGLE-CLOUD-IOT-iMX7-QSG.pdf 
# STM32 board, NXP, TI etc Uboot- Universal bootloader
<img width="1078" height="438" alt="image" src="https://github.com/user-attachments/assets/399c57e2-0cbd-46e6-a7f1-d22f7ee209c2" />

<img width="1078" height="438" alt="image" src="https://github.com/user-attachments/assets/41ee8d37-4058-4318-8c18-6bc32476a8a1" />
```
What is bootloader?
software that helps in initial startup of the system
platform specific and hardware dependend
Bootloader act as a bridge between HW and user Software. They are  essential for
flexibility, security and lifecycle management of devices. whether it is a Toaster or tesla,
their is likely a bootloader is involved.
```

<img width="1078" height="438" alt="image" src="https://github.com/user-attachments/assets/da7e901c-7306-4da9-b45e-c4eac81ce69f" />

<img width="1129" height="605" alt="image" src="https://github.com/user-attachments/assets/c1b28a3e-8ca0-4e03-8b51-1c4c7083a7b8" />

<img width="1129" height="290" alt="image" src="https://github.com/user-attachments/assets/927b1938-0994-47b3-ad80-b0640bba31be" />


<img width="1129" height="290" alt="image" src="https://github.com/user-attachments/assets/b4656566-f390-4814-80d1-499b25f54c66" />

## am335x block diagram
<img width="1059" height="1100" alt="image" src="https://github.com/user-attachments/assets/795ad581-55f4-40a4-a8fc-4775b328a37b" /> 

## du -sh linux_6.16.6/arch/arm/boot/zimage 
### 5.4MB zimage
<img width="1129" height="516" alt="image" src="https://github.com/user-attachments/assets/f5884466-862a-4e26-990a-827108c52093" />

<img width="1129" height="503" alt="image" src="https://github.com/user-attachments/assets/8b20693f-a540-4a7b-b916-f6f4974b2f85" />

<img width="1140" height="605" alt="image" src="https://github.com/user-attachments/assets/839a7772-462c-486a-9fcc-74449e0f0acd" />

## ARM Cortex Toolchain
## sudo apt install gcc-arm-none-eabi


# second zes
## normally the object files
## cmd
  ### objdump -h a.out
<img width="1140" height="544" alt="image" src="https://github.com/user-attachments/assets/d2753d6b-df0f-4237-89d3-483e9a792e0c" />

## FIRST WE HAVE TALK TO LINKER SCRIPT
<img width="1140" height="544" alt="image" src="https://github.com/user-attachments/assets/e1d1a40c-1b44-43e7-aad7-67b2d5e8fb8d" />
<img width="1140" height="625" alt="image" src="https://github.com/user-attachments/assets/3c6655c8-b419-4394-8766-eb13c28d978e" />

<img width="1092" height="452" alt="image" src="https://github.com/user-attachments/assets/0b92b11d-2a84-4d39-b353-878ab24ee0cb" />

<img width="1125" height="591" alt="image" src="https://github.com/user-attachments/assets/d3e1cc11-9ce9-4cbc-9aa9-91576658555f" />

<img width="1125" height="331" alt="image" src="https://github.com/user-attachments/assets/983ca38f-4f59-45fa-8afc-772b7a7a0c74" />
<img width="1125" height="581" alt="image" src="https://github.com/user-attachments/assets/fe5a5287-edb1-40c5-8820-790007338f7c" />
<img width="1186" height="654" alt="image" src="https://github.com/user-attachments/assets/0d46d5aa-3b1b-4e76-94a7-b84a7d6aae90" /> 
## make burn
<img width="1172" height="394" alt="image" src="https://github.com/user-attachments/assets/e1acb047-cbc6-42b9-af7f-b3ab0e8360b0" />

<img width="1172" height="454" alt="image" src="https://github.com/user-attachments/assets/4965bca3-bc23-41fc-bc21-1a7a87a2612d" />

<img width="1172" height="454" alt="image" src="https://github.com/user-attachments/assets/f68bfa18-0d0a-45d7-bbcb-7bfb5c367b15" />
<img width="1172" height="368" alt="image" src="https://github.com/user-attachments/assets/c77122a8-4b8e-4c85-ba20-aa1681c87756" />
<img width="1172" height="519" alt="image" src="https://github.com/user-attachments/assets/fd417055-2e11-4755-96db-5842db3500fb" />
<img width="1172" height="371" alt="image" src="https://github.com/user-attachments/assets/6723fb93-648d-4303-8e10-eaefddb6c96a" />

<img width="1172" height="261" alt="image" src="https://github.com/user-attachments/assets/243d900f-08ab-48d9-8fe8-5512576e9aa3" />
<img width="1172" height="261" alt="image" src="https://github.com/user-attachments/assets/6f4072c4-1677-4ce3-847a-f06ea53c6615" />

<img width="793" height="426" alt="image" src="https://github.com/user-attachments/assets/90dd0022-187a-4caa-9f92-3dbdcea5f37c" />
<img width="979" height="248" alt="image" src="https://github.com/user-attachments/assets/820007b4-ac21-4d85-91c1-5e81b1f60d56" />
<img width="1066" height="315" alt="image" src="https://github.com/user-attachments/assets/cc3a9db2-1579-4aa1-8842-d6566262265e" />
<img width="1066" height="315" alt="image" src="https://github.com/user-attachments/assets/14b21db6-bd2d-45cf-b418-a233939ddd67" />
<img width="1066" height="315" alt="image" src="https://github.com/user-attachments/assets/c6877002-9ad8-454f-923a-c5e21a8036ea" />
<img width="1066" height="315" alt="image" src="https://github.com/user-attachments/assets/10e70563-b2c0-4f92-ab76-2f64082887a7" />


<img width="1140" height="605" alt="image" src="https://github.com/user-attachments/assets/73c6f9ae-1e27-4027-ada2-737b9682cd60" />
## Linux@thanga$: size a.out
<img width="457" height="40" alt="image" src="https://github.com/user-attachments/assets/44352e99-dcc3-4ae1-b3d7-ea5a351dddc1" />



<img width="1092" height="452" alt="image" src="https://github.com/user-attachments/assets/c21be661-9526-4725-8fcf-1456b402c667" />
<img width="1066" height="315" alt="image" src="https://github.com/user-attachments/assets/19e1b3e8-14ce-42ce-8b10-95485fde1346" />
<img width="1066" height="250" alt="image" src="https://github.com/user-attachments/assets/89773e4e-dd7a-4913-8d6c-1a4a3ae52ab4" />
<img width="1066" height="271" alt="image" src="https://github.com/user-attachments/assets/586395a2-753c-422c-9ca4-5526fabb77d4" />
<img width="1137" height="598" alt="image" src="https://github.com/user-attachments/assets/d0bbb313-98c7-428d-a597-b7b208b155a2" />
<img width="1137" height="598" alt="image" src="https://github.com/user-attachments/assets/85cf8a9a-0b5b-4517-9b91-070e98bbbe64" />
<img width="1110" height="274" alt="image" src="https://github.com/user-attachments/assets/7480f28a-6798-41e8-9138-676f472c271a" />
<img width="1110" height="613" alt="image" src="https://github.com/user-attachments/assets/b0412f7c-1822-4406-bc2d-4c1f952807ec" />
<img width="1110" height="526" alt="image" src="https://github.com/user-attachments/assets/b359e636-3b5d-4a5d-9c38-7069de0e7407" />
<img width="1110" height="526" alt="image" src="https://github.com/user-attachments/assets/56f5f97b-1425-44f2-95db-122c03c5deeb" />
<img width="1110" height="526" alt="image" src="https://github.com/user-attachments/assets/72cff9ce-2ca0-4612-bdc4-6746d327d1f1" />
<img width="1110" height="377" alt="image" src="https://github.com/user-attachments/assets/2e505f1d-0f5b-434b-8647-e0a795d2ba12" />

# https://github.com/ferenc-nemeth/stm32-bootloader?tab=readme-ov-file















