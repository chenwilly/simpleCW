# - * - coding: utf-8 - * -
dari impor  linep *
impor json, waktu, acak

client = LineClient ()
# client = LineClient (authToken = 'AUTH TOKEN')
client.log ( " Auth Token: "  +  str (client.authToken))

channel = LineChannel (klien)
client.log ( " Channel Access Token: "  +  str (channel.channelAccessToken))

jajak pendapat = LinePoll (klien)

cctv = {
    " cyduk " : {},
    " titik " : {},
    " sidermem " : {}
}

sementara  True :
    coba :
        ops = poll.singleTrace ( hitungan = 50 )
        untuk op di ops:
            jika op.type ==  26 :
                msg = op.message
                jika msg.text ! =  Tidak ada :
                    jika msg.toType ==  2 :
                        mungkin = client.getProfile (). pertengahan
                        jika Mei di  str (msg.contentMetadata) dan  ' MENYEBUTKAN '  di  str (msg.contentMetadata):
                            pilih = [ ' yang tag sy semoga jomblo seumur hidup ' , ' ngapain tag tag woe, kangen? ' , ' ada apa ini? tag ko di? ' , ' duhh kena tag, dianya kesepian kali yah ' , ' gk usah tag, hadiah tikel aja ' ]
                            rslt = random.choice (pilih)
                            client.sendText (msg.to, str (rslt))
                        lain :
                            lulus
                    lain :
                        lulus
                lain :
                    lulus
            elif op.type ==  25 :
                msg = op.message
                text = msg.text
                msg_id = msg.id
                penerima = msg. untuk
                pengirim = msg._from
                coba :
                    jika msg.contentType ==  0 :
                        jika msg.toType ==  2 :
                            client.sendChatChecked (penerima, msg_id)
                            contact = client.getContact (pengirim)
                            if text.lower () ==  ' me ' :
                                client.sendMessage (receiver, None , contentMetadata = { ' mid ' : sender}, contentType = 13 )
                            elif text.lower () ==  ' speed ' :
                                start = time.time ()
                                client.sendText (penerima, " TestSpeed " )
                                elapsed_time = time.time () - mulai
                                client.sendText (receiver, " % s detik "  % (elapsed_time))
                            elif  ' spic '  di text.lower ():
                                coba :
                                    key =  eval (msg.contentMetadata [ " PERHATIAN " ])
                                    u = kunci [ " MENTIONEES " ] [ 0 ] [ " M " ]
                                    a = client.getContact (u) .pictureStatus
                                    client.sendImageWithURL (receiver, ' http://dl.profile.line.naver.jp/ ' + a)
                                kecuali  Exception  sebagai e:
                                    client.sendText (receiver, str (e))
                            elif  ' scover '  di text.lower ():
                                coba :
                                    key =  eval (msg.contentMetadata [ " PERHATIAN " ])
                                    u = kunci [ " MENTIONEES " ] [ 0 ] [ " M " ]
                                    a = channel.getProfileCoverURL ( mid = u)
                                    client.sendImageWithURL (receiver, a)
                                kecuali  Exception  sebagai e:
                                    client.sendText (receiver, str (e))
                            elif text.lower () ==  ' tagall ' :
                                group = client.getGroup (msg.to)
                                nama = [contact.mid untuk kontak dalam group.members]
                                nm1, nm2, nm3, nm4, nm5, jml = [], [], [], [], [], len (nama)
                                jika jml <=  100 :
                                    client.mention (msg.to, nama)
                                jika jml >  100  dan jml <  200 :
                                    untuk i dalam  rentang ( 0 , 100 ):
                                        nm1 + = [nama [i]]
                                    client.mention (msg.to, nm1)
                                    untuk j di  kisaran ( 101 , len (nama)):
                                        nm2 + = [nama [j]]
                                    client.mention (msg.to, nm2)
                                jika jml >  200  dan jml <  300 :
                                    untuk i dalam  rentang ( 0 , 100 ):
                                        nm1 + = [nama [i]]
                                    client.mention (msg.to, nm1)
                                    untuk j di  kisaran ( 101 , 200 ):
                                        nm2 + = [nama [j]]
                                    client.mention (msg.to, nm2)
                                    untuk k dalam  jangkauan ( 201 , len (nama)):
                                        nm3 + = [nama [k]]
                                    client.mention (msg.to, nm3)
                                jika jml >  300  dan jml <  400 :
                                    untuk i dalam  rentang ( 0 , 100 ):
                                        nm1 + = [nama [i]]
                                    client.mention (msg.to, nm1)
                                    untuk j di  kisaran ( 101 , 200 ):
                                        nm2 + = [nama [j]]
                                    client.mention (msg.to, nm2)
                                    untuk k dalam  jangkauan ( 201 , len (nama)):
                                        nm3 + = [nama [k]]
                                    client.mention (msg.to, nm3)
                                    untuk l di  kisaran ( 301 , len (nama)):
                                        nm4 + = [nama [l]]
                                    client.mention (msg.to, nm4)
                                jika jml >  400  dan jml <  501 :
                                    untuk i dalam  rentang ( 0 , 100 ):
                                        nm1 + = [nama [i]]
                                    client.mention (msg.to, nm1)
                                    untuk j di  kisaran ( 101 , 200 ):
                                        nm2 + = [nama [j]]
                                    client.mention (msg.to, nm2)
                                    untuk k dalam  jangkauan ( 201 , len (nama)):
                                        nm3 + = [nama [k]]
                                    client.mention (msg.to, nm3)
                                    untuk l di  kisaran ( 301 , len (nama)):
                                        nm4 + = [nama [l]]
                                    client.mention (msg.to, nm4)
                                    untuk m di  kisaran ( 401 , len (nama)):
                                        nm5 + = [nama [m]]
                                    client.mention (msg.to, nm5)             
                                client.sendText (penerima, " Anggota: " + str (jml))
                            elif text.lower () ==  ' ceksider ' :
                                coba :
                                    del cctv [ ' titik ' ] [msg.to]
                                    del cctv [ ' sidermem ' ] [msg.to]
                                    del cctv [ ' cyduk ' ] [msg.to]
                                kecuali :
                                    lulus
                                cctv [ ' point ' ] [msg.to] = msg.id
                                cctv [ ' sidermem ' ] [msg.to] =  " "
                                cctv [ ' cyduk ' ] [msg.to] = Benar
                            elif text.lower () ==  ' offread ' :
                                jika msg.to in cctv [ ' point ' ]:
                                    cctv [ ' cyduk ' ] [msg.to] = Salah
                                    client.sendText (msg.to, cctv [ ' sidermem ' ] [msg.to])
                                lain :
                                    client.sendText (msg.to, " Heh belom di Set " )
                kecuali  Exception  sebagai e:
                    client.log ( " [SEND_MESSAGE] ERROR: "  +  str (e))

            elif op.type == OpType. NOTIFIED_READ_MESSAGE :
                coba :
                    jika cctv [ ' cyduk ' ] [op.param1] == Benar :
                        jika op.param1 dalam cctv [ ' point ' ]:
                            Nama = client.getContact (op.param2) .displayName
                            jika Nama dalam cctv [ ' sidermem ' ] [op.param1]:
                                lulus
                            lain :
                                cctv [ ' sidermem ' ] [op.param1] + =  " \ n ~ "  + Nama
                                pref = [ ' eh ada ' , ' hai kak ' , ' aloo .. ' , ' nah ' , ' lg ngapain ' , ' halo ' , ' sini kak ' ]
                                client.sendText (op.param1, str (random.choice (pref)) + '  ' + Nama)
                        lain :
                            lulus
                    lain :
                        lulus
                kecuali :
                    lulus

            lain :
                lulus

            # Jangan hapus baris ini, jika Anda tidak segera mendapatkan kesalahan!
            poll.setRevision (op.revision)
            
    kecuali  Exception  sebagai e:
        client.log ( " [SINGLE_TRACE] ERROR: "  +  str
