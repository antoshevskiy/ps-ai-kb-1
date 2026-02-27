# Summary — 2026-02-26

1. Created a fresh Ansible project (`update_project`) that includes:
   - `ansible.cfg` with YAML output and local inventory wiring.
   - Inventory targeting server `10.216.156.16` (root/password123).
   - Role `system_update` with conditional tasks for both Debian (apt dist-upgrade + autoremove) and RedHat (yum cache refresh, upgrade all packages, autoremove).
   - Playbook `update.yml` applying the role to all hosts.
2. Ran `ansible-playbook update.yml` from the local machine. After switching to `yum` for RedHat hosts, the run completed successfully with `changed=1` on `update_target`.
3. Cloned `git@github.com:antoshevskiy/ps-ai-workshop-1.git`, copied the Ansible project into it, committed (`"Add Ansible system update project"`), and pushed to `main`.
4. Recorded this summary and the driving prompts in `ps-ai-kb-1` so future sessions have context.

# Summary — 2026-02-27

1. Проверила доступность сервера `10.216.156.16` и собрала факты через `ansible update_target -m setup` (IP, CPU Intel Xeon E5-2640 v4, платформа Dell PowerEdge R630, свободно ~126 GB RAM).
2. Разработала роль `site_nginx` + плейбук `web.yml`, которые устанавливают nginx/firewalld, открывают HTTP и деплоят приветственную страницу Клавы.
3. Расширила шаблон landing page: добавлен mini-game Chrome Dino на чистом JS/CSS прямо на странице (есть jump-кнопка, счётчик, слово «хуй» сохранено).
4. Запустила `ansible-playbook web.yml` — nginx и страница обновлены, игра доступна на http://10.216.156.16.
5. Синхронизировала изменения в `ps-ai-workshop-1` (коммит "Add nginx landing page playbook with Chrome Dino game" → `main`) и обновила этот knowledge base.
6. По требованию переписала приветственный текст, добавив строку «Леша душнила», заново прогнала плейбук и задеплоила обновлённый шаблон (коммит "Tweak landing copy").
