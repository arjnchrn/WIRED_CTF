# w!r3d_sh4rk
unzipped the gz package using gzip -d<br>
opened the decompressed pcapng file in wireshark<br>
following a TCP stream showed an indication of the flag as "flag-is-wireshark-is-cool.my.canva.site" was a string hidden in the stream<br>
destination ip is 103.169.142.250 but cloudflare prevents direct ip access. So going to flag-is-wireshark-is-cool.my.canva.site was the only option (aside from the flag obviously being in the name)<br>
website flag-is-wireshark-is-cool.my.canva.site prints out the flag flag{wireshark_is_cool}<br>
