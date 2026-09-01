
## ⏰ Scheduler

WebWatch uses **APScheduler** to automatically monitor websites at regular intervals.

### Scheduler Code

''`python
from apscheduler.schedulers.background import BackgroundScheduler
from monitor import monitor_websites

scheduler = BackgroundScheduler()


def start_scheduler():
    scheduler.add_job(
        monitor_websites,
        trigger="interval",
        minutes=1,
        id="website_monitor",
        replace_existing=True
    )

    scheduler.start()

    print("WebWatch Scheduler Started")
    print("Monitoring websites every 1 minute")


def stop_scheduler():
    scheduler.shutdown()
    print("WebWatch Scheduler Stopped")
