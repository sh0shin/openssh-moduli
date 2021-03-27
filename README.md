[//]: # ( vim: set ft=markdown : )
# OpenSSH Moduli

Collection of "safe" moduli(5) for SSH hardening.

## Generate
```bash
# OpenSSH >= 8.2
for MODULI_BITS in {3072..8192..1024}
do
  ssh-keygen -M generate -O bits="$MODULI_BITS" "moduli-$MODULI_BITS.candidates" && \
  ssh-keygen -M screen -f "moduli-$MODULI_BITS.candidates" "moduli-$MODULI_BITS"
done
```

```bash
# OpenSSH < 8.2
for MODULI_BITS in {3072..8192..1024}
do
  ssh-keygen -G "moduli-$MODULI_BITS.candidates" -b "$MODULI_BITS" && \
  ssh-keygen -T "moduli-$MODULI_BITS" -f "moduli-$MODULI_BITS.candidates"
done
```

See man ssh-keygen(1) MODULI GENERATION section for details.
