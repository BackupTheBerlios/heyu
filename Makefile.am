#
# Makefile.am - Automake source file for Heyu
#
# Copyright (C) 2011 Janusz Krzysztofik <jkrzyszt@tis.icnet.pl>
#
#   This program is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

bin_PROGRAMS = heyu
heyu_SOURCES = date.c erase.c info.c  message.c relay.c \
	monitor.c reset.c setclock.c stop.c \
	tty.c x10.c xread.c xwrite.c status.c cm11a.c \
	eeprom.c process.c sun.c cmd.c config.c x10state.c \
	poll.c modules.c cm17a.c xsync.c timing.c cm10a.c \
	tty_aux.c relay_aux.c x10aux.c rfxcom.c digimax.c oregon.c \
	x10.h eeprom.h process.h sun.h x10state.h \
	rfxcom.h digimax.h oregon.h
dist_man_MANS = heyu.1 x10config.5 x10sched.5 x10scripts.5 x10cm17a.5 x10aux.5 \
	x10rfxsensors.5 x10rfxmeters.5 x10digimax.5 x10oregon.5 x10kaku.5
dist_doc_DATA = README README1 README2 protocol.txt history.txt heyufaq.txt \
	AUTHORS COPYING INSTALL README.cm10a README.webhook release_notes.txt
dist_pkgsysconf_DATA = x10config.sample x10.sched.sample
EXTRA_DIST = Configure.sh post-install.sh

@MAN1DIR@
@MAN5DIR@

*.o: Makefile

if POSTINST
all-local: usergroup.tmp userhome.tmp

usergroup.tmp userhome.tmp: $(bin_PROGRAMS)
	@echo `id` >usergroup.tmp
	@echo ${HOME}  >userhome.tmp
	@echo ""
	@echo "**Now become root and run 'make install' **"
	@echo ""

install-exec-hook:
	@$(POST_INSTALL)
	@POSTINST@
endif
